---
title: "Validation d&#39;une transaction en une phase unique et en plusieurs phases  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Validation d&#39;une transaction en une phase unique et en plusieurs phases 
Les ressources utilisées dans une transaction sont gérées par un gestionnaire de ressources, dont les actions sont coordonnées par un gestionnaire de transactions.La rubrique [Inscription de ressources comme participants à une transaction ](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) explique comment inscrire une ressource \(ou plusieurs ressources\) à une transaction.Elle traite de la coordination de la validation d'une transaction entre les ressources inscrites.  
  
 À la fin de la transaction, l'application requiert la validation ou la restauration de la transaction.Le gestionnaire de transactions doit éliminer tous les risques, par exemple des gestionnaires de ressources votant pour la validation de la transaction et d'autres votant pour sa restauration.  
  
 Si votre transaction implique plusieurs ressources, vous devez effectuer une validation en deux phases \(2PC\).Le protocole de validation en deux phases \(une phase de préparation et une phase de validation\) garantit, à la fin de la transaction, l'entière validation ou restauration de l'ensemble des modifications apportées aux ressources.Tous les participants sont ensuite informés du résultat final.Pour une présentation détaillée du protocole de validation en deux phases, consultez « *Transaction Processing : Concepts and Techniques \(Morgan Kaufmann Series in Data Management Systems\) ISBN:1558601902* » de Jim Gray.  
  
 Vous pouvez également optimiser les performances de votre transaction en suivant le protocole de validation en une phase.Pour plus d'informations, consultez [Optimisation à l'aide de la validation à phase unique et de la notification de phase unique pouvant être promue ](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 Pour être informé du résultat d'une transaction sans participer au vote, inscrivez\-vous à l'événement <xref:System.Transactions.Transaction.TransactionCompleted>.  
  
## Validation en deux phases \(2PC\)  
 Lors de la première phase de transaction, le gestionnaire de transactions interroge chaque ressource afin de déterminer si la transaction doit être validée ou restaurée.Lors de la seconde phase de transaction, le gestionnaire de transactions informe chaque ressource du résultat de ses recherches, lui permettant d'effectuer les nettoyages nécessaires.  
  
 Pour participer à ce type de transaction, un gestionnaire de ressources doit implémenter l'interface <xref:System.Transactions.IEnlistmentNotification>, qui fournit des méthodes appelées par le gestionnaire de transactions en tant que notifications, au cours d'une validation en deux phases \(2PC\).L'exemple suivant illustre une implémentation de ce type.  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### Phase de préparation \(Phase 1\)  
 À la réception d'une requête <xref:System.Transactions.CommittableTransaction.Commit%2A> de l'application, le gestionnaire de transactions lance la phase de préparation des participants inscrits en appelant la méthode <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> sur chaque ressource inscrite, afin d'obtenir leur vote concernant la transaction.  
  
 Le gestionnaire de ressources qui implémente l'interface <xref:System.Transactions.IEnlistmentNotification> doit d'abord implémenter la méthode <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29>, comme illustré par l'exemple simple suivant.  
  
```  
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
  
```  
  
 Lorsque le gestionnaire de ressources durables reçoit cet appel, il doit consigner les informations de récupération de la transaction \(disponibles par récupération de la propriété <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A>\) ainsi que l'ensemble des informations nécessaires pour terminer la transaction en cours de validation.Il n'est pas nécessaire d'effectuer cette opération au sein de la méthode <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> car le gestionnaire de ressources peut le faire sur un thread de travail.  
  
 Une fois que le gestionnaire de ressources a terminé son travail de préparation, il doit voter pour la validation ou la restauration en appelant la méthode <xref:System.Transactions.PreparingEnlistment.Prepared%2A> ou <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A>.Notez que la classe <xref:System.Transactions.PreparingEnlistment> hérite d'une méthode <xref:System.Transactions.Enlistment.Done%2A> de la classe <xref:System.Transactions.Enlistment>.L'appel à cette méthode sur le rappel <xref:System.Transactions.PreparingEnlistment> au cours de la phase de préparation indique au gestionnaire de transactions qu'il s'agit d'une inscription en lecture seule \(des gestionnaires de ressources qui peuvent être lus mais qui ne peuvent pas mettre à jour les données protégées par la transaction\) et le gestionnaire de ressources ne reçoit plus de notification du gestionnaire de transaction jusqu'au résultat de la transaction en phase 2.  
  
 L'application est informée de la validation réussie de la transaction après le vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A> de tous les gestionnaires de ressources  
  
### Phase de validation \(Phase 2\)  
 Lors de la seconde phase de la transaction, si le gestionnaire de transactions a reçu les préparations réussies de tous les gestionnaires de ressources \(c'est\-à\-dire, si tous les gestionnaires de ressources ont appelé <xref:System.Transactions.PreparingEnlistment.Prepared%2A> à la fin de la phase 1\), il appelle la méthode <xref:System.Transactions.IEnlistmentNotification.Commit%2A> pour chaque gestionnaire de ressources.Les gestionnaires de ressources peuvent ensuite confirmer les modifications et terminer la validation.  
  
 Si l'un des gestionnaires de ressources signale un échec de préparation en phase 1, le gestionnaire de transactions appelle la méthode <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> pour chaque gestionnaire de ressources et communique l'échec de la validation à l'application.  
  
 C'est pourquoi votre gestionnaire de ressources doit implémenter les méthodes suivantes.  
  
```  
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment    
     enlistment.Done();    
}  
```  
  
 Le gestionnaire de ressources doit effectuer le nécessaire pour terminer la transaction d'après le type de notification, puis en informer le gestionnaire de transactions en appelant la méthode <xref:System.Transactions.Enlistment.Done%2A> sur le paramètre <xref:System.Transactions.Enlistment>.Cela peut s'effectuer sur un thread de travail.Notez que les notifications de la phase 2 peuvent se produire en ligne sur le même thread qui a appelé la méthode <xref:System.Transactions.PreparingEnlistment.Prepared%2A> de la phase 1.Par conséquent, vous ne devez effectuer aucun travail après l'appel <xref:System.Transactions.PreparingEnlistment.Prepared%2A> \(par exemple, libérer des verrous\) que vous devez avoir terminé avant de recevoir les notifications de phase 2.  
  
### Implémentation de la méthode InDoubt  
 Enfin, implémentez la méthode <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> pour le gestionnaire de ressources volatiles.Cette méthode est appelée si le gestionnaire de transactions perd contact avec un ou plusieurs participants, rendant leur état inconnu.Dans ce cas, consignez ce fait afin de pouvoir ensuite contrôler si des participants à la transaction ont été laissés dans un état incohérent.  
  
```  
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## Optimisation de la validation en une phase  
 Le protocole de validation en une phase est plus efficace lors de l'exécution, car toutes les mises à jour sont effectuées sans coordination explicite.Pour plus d'informations sur ce protocole, consultez [Optimisation à l'aide de la validation à phase unique et de la notification de phase unique pouvant être promue ](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
## Voir aussi  
 [Optimisation à l'aide de la validation à phase unique et de la notification de phase unique pouvant être promue ](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)   
 [Inscription de ressources comme participants à une transaction ](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)