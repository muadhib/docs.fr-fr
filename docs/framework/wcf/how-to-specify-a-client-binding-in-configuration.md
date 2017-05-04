---
title: "Comment&#160;: sp&#233;cifier une liaison de client dans la configuration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Comment&#160;: sp&#233;cifier une liaison de client dans la configuration
Dans cet exemple, une application console cliente est créée pour utiliser un service de calculatrice, et la liaison pour ce client est spécifiée de façon déclarative dans la configuration. Le client accède à la `CalculatorService`, qui implémente le `ICalculator` interface, le service et le client utilisent le <xref:System.ServiceModel.BasicHttpBinding> classe.  
  
 La procédure présentée suppose que le service de calculatrice est en cours d'exécution. Pour plus d’informations sur la création du service, consultez [Comment : spécifier une liaison de Service dans la Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Il utilise également la [Service Model Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) qui [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] pour générer automatiquement les composants clients. L'outil génère le code client et la configuration permettant d'accéder au service.  
  
 La construction du client se divise en deux parties. L'outil Svcutil.exe génère la calculatrice `ClientCalculator` qui implémente l'interface `ICalculator`. Cette application cliente est ensuite construite à l'aide d'une instance de `ClientCalculator`.  
  
 Il est généralement conseillé de spécifier de façon déclarative les informations de liaison et d'adresse dans la configuration plutôt que de manière impérative dans le code. La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service. Plus généralement, le fait de laisser les informations de liaison et d’adresse hors du code leur permet de changer sans nécessiter de recompilation ou de redéploiement de l’application.  
  
 Vous pouvez effectuer toutes les étapes de configuration suivantes à l’aide de la [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Pour la copie de la source de cet exemple, consultez la [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) exemple.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Spécification d’une liaison de client dans la configuration  
  
1.  Utilisez l'outil Svcutil.exe depuis la ligne de commande pour générer le code à partir des métadonnées de service.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Le client généré contient l'interface `ICalculator` qui définit le contrat de service auquel l'implémentation du client doit satisfaire.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  Le client généré contient également l'implémentation de `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  SvcUtil.exe génère également la configuration du client qui utilise le <xref:System.ServiceModel.BasicHttpBinding> classe. Lorsque vous utilisez [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], nommez ce fichier App.config. Notez que les informations d'adresse et de liaison ne sont pas spécifiées n'importe où à l'intérieur de l'implémentation du service. Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.  
  
     <!-- TODO: review snippet reference [!code[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/common/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]  -->  
  
5.  Créez une instance de `ClientCalculator` dans une application, puis appelez les opérations de service.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  Compilez, puis exécutez le client.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de liaisons pour configurer les Services et les Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)