---
title: "Procédure pas à pas : utilisation de procédures stockées uniquement (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 800cc7d6a1e4aa836ebe75afcbe29a3532ee173a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a>Procédure pas à pas : utilisation de procédures stockées uniquement (Visual Basic)
Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de base complet pour accéder aux données à l'aide de procédures stockées uniquement. Cette approche est souvent utilisée par les administrateurs de base de données pour limiter les moyens d'accès au magasin de données.  
  
> [!NOTE]
>  Vous pouvez également utiliser des procédures stockées dans les applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour substituer le comportement par défaut, plus particulièrement pour les processus `Create`, `Update` et `Delete`. Pour plus d’informations, consultez [personnalisation des opérations d’insertion, mise à jour et supprimer](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Dans cette procédure pas à pas, vous utiliserez deux méthodes mappées aux procédures stockées dans l'exemple de base de données Northwind : CustOrdersDetail et CustOrderHist. Le mappage se produit lorsque vous exécutez l'outil en ligne de commande SQLMetal pour générer un fichier [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]. Pour plus d'informations, consultez la section Composants requis par la suite dans cette procédure pas à pas.  
  
 Cette procédure pas à pas ne s'appuie pas sur le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent également utiliser le [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] pour implémenter les fonctionnalités de procédure stockée. Consultez [LINQ to SQL des outils dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual Basic.  
  
## <a name="prerequisites"></a>Prérequis  
 Elle requiert les éléments suivants :  
  
-   Les fichiers sont stockés dans un dossier dédié, c:\linqtest3. Vous devez créer ce dossier avant de commencer la procédure pas à pas.  
  
-   Exemple de base de données Northwind.  
  
     Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest3.  
  
-   Fichier de code [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] généré à partir de la base de données Northwind.  
  
     Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :  
  
     **sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**  
  
     Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Vue d'ensemble  
 Cette procédure pas à pas se compose de six tâches principales :  
  
-   Configuration de la solution [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dans [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
-   Ajout de l'assembly System.Data.Linq au projet.  
  
-   Ajout du fichier de code de base de données au projet.  
  
-   Création d'une connexion à la base de données.  
  
-   Configuration de l'interface utilisateur.  
  
-   Exécution et test de l'application.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Création d'une solution LINQ to SQL  
 Au cours de cette première tâche, vous allez créer une solution [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] qui contient les références nécessaires pour générer et exécuter un projet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Pour créer une solution LINQ to SQL  
  
1.  Sur le [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **fichier** menu, cliquez sur **nouveau projet**.  
  
2.  Dans le volet **Types de projets** dans la boîte de dialogue **Nouveau projet** , développez **Visual Basic**, puis cliquez sur **Windows**.  
  
3.  Dans le volet **Modèles** , cliquez sur **Application Windows Forms**.  
  
4.  Dans le **nom** , tapez **SprocOnlyApp**.  
  
5.  Cliquez sur **OK**.  
  
     Le Concepteur Windows Forms s'ouvre.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>Ajout de la référence à l'assembly LINQ to SQL  
 L'assembly [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] n'est pas inclus dans le modèle Application Windows Forms standard. Vous devrez ajouter l'assembly vous-même, comme expliqué dans les étapes suivantes :  
  
#### <a name="to-add-systemdatalinqdll"></a>Pour ajouter System.Data.Linq.dll  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur **afficher tous les fichiers**.  
  
2.  Dans **l’Explorateur de solutions**, avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.  
  
3.  Dans le **ajouter une référence** boîte de dialogue, cliquez sur **.NET**et cliquez sur l’assembly System.Data.Linq, puis cliquez sur **OK**.  
  
     L'assembly est ajouté au projet.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Ajout du fichier de code Northwind au projet  
 Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind. Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Pour ajouter le fichier de code Northwind au projet  
  
1.  Sur le **projet** menu, cliquez sur **ajouter un élément existant**.  
  
2.  Dans le **ajouter un élément existant** boîte de dialogue, accédez à c:\linqtest3\northwind.vb, puis cliquez sur **ajouter**.  
  
     Le fichier northwind.vb est ajouté au projet.  
  
## <a name="creating-a-database-connection"></a>Création d'une connexion à une base de données  
 Au cours de cette étape, vous allez définir la connexion à l'exemple de base de données Northwind. Cette procédure pas à pas utilise "c:\linqtest3\northwnd.mdf" comme chemin d'accès.  
  
#### <a name="to-create-the-database-connection"></a>Pour créer la connexion de base de données  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **Form1.vb**, puis cliquez sur **afficher le Code**.  
  
     `Class Form1` apparaît dans l'éditeur de code.  
  
2.  Tapez le code suivant dans le bloc de code `Form1` :  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a>Configuration de l'interface utilisateur.  
 Au cours de cette tâche, vous allez créez une interface pour permettre aux utilisateurs d'exécuter des procédures stockées pour accéder aux données de la base de données. Dans l'application que vous développez avec cette procédure pas à pas, les utilisateurs peuvent accéder aux données de la base de données uniquement en utilisant les procédures stockées incorporées dans l'application.  
  
#### <a name="to-set-up-the-user-interface"></a>Pour configurer l'interface utilisateur  
  
1.  Revenir à la fenêtre Concepteur de formulaires (**Form1.vb]**).  
  
2.  Dans le menu **Affichage** , cliquez sur **Boîte à outils**.  
  
     La boîte à outils s'ouvre.  
  
    > [!NOTE]
    >  Cliquez sur le **masquage automatique** punaise pour garder la boîte à outils ouverte pendant que vous effectuez les autres étapes de cette section.  
  
3.  Faites glisser deux boutons, deux zones de texte et deux étiquettes à partir de la boîte à outils vers **Form1**.  
  
     Disposez les contrôles comme dans l'illustration associée. Développez **Form1** afin que les contrôles s’ajustent facilement.  
  
4.  Avec le bouton droit **Label1**, puis cliquez sur **propriétés**.  
  
5.  Modifier la **texte** propriété à partir de **Label1** à **Enter OrderID :**.  
  
6.  Dans la même façon pour **Label2**, modifiez le **texte** propriété à partir de **Label2** à **Enter CustomerID :**.  
  
7.  Dans la même façon, modifiez le **texte** propriété **Button1** à **Order Details**.  
  
8.  Modifier la **texte** propriété **Button2** à **l’historique des commandes**.  
  
     Élargissez les contrôles boutons afin que tout le texte soit visible.  
  
#### <a name="to-handle-button-clicks"></a>Pour gérer des clics de bouton  
  
1.  Double-cliquez sur **Order Details** sur **Form1** pour créer le `Button1` Gestionnaire d’événements et ouvrez l’éditeur de code.  
  
2.  Tapez le code suivant dans le gestionnaire d'événements `Button1` :  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  Double-cliquez maintenant sur **Button2** sur Form1 pour créer le `Button2` Gestionnaire d’événements et ouvrez l’éditeur de code.  
  
4.  Tapez le code suivant dans le gestionnaire d'événements `Button2` :  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous allez maintenant tester votre application. Notez que votre contact avec le magasin de données est limité aux actions que les deux procédures stockées peuvent accepter. Ces actions consistent à retourner les produits inclus pour n'importe quel orderID que vous entrez ou à retourner un historique des produits commandés pour n'importe quel CustomerID que vous entrez.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Appuyez sur F5 pour démarrer le débogage.  
  
     Form1 s'affiche.  
  
2.  Dans le **Enter OrderID** , tapez **10249** puis cliquez sur **Order Details**.  
  
     Un message répertorie les produits inclus dans la commande 10249.  
  
     Cliquez sur **OK** pour fermer la boîte de message.  
  
3.  Dans le **Enter CustomerID** , tapez `ALFKI`, puis cliquez sur **l’historique des commandes**.  
  
     Un message répertorie l'historique des commandes pour le client ALFKI.  
  
     Cliquez sur **OK** pour fermer la boîte de message.  
  
4.  Dans le **Enter OrderID** , tapez `123`, puis cliquez sur **Order Details**.  
  
     Le message suivant s'affiche : « Aucun résultat ».  
  
     Cliquez sur **OK** pour fermer la boîte de message.  
  
5.  Sur le **déboguer** menu, cliquez sur **arrêter le débogage**.  
  
     La session de débogage s'arrête.  
  
6.  Si vous avez terminé les tests, vous pouvez cliquer sur **fermer le projet** sur la **fichier** menu et enregistrez votre projet lorsque vous y êtes invité.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous pouvez améliorer ce projet en apportant des modifications. Par exemple, vous pouvez répertorier les procédures stockées disponibles dans une zone de liste et demander à l'utilisateur de sélectionner les procédures à exécuter. Vous pouvez également transmettre en continu la sortie des rapports dans un fichier texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
