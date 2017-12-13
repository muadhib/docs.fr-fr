---
title: "Développement de pipeline"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4991fc65a48d620d30d09c44f1a30c2d1839071e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="pipeline-development"></a><span data-ttu-id="fb677-102">Développement de pipeline</span><span class="sxs-lookup"><span data-stu-id="fb677-102">Pipeline Development</span></span>
<span data-ttu-id="fb677-103">Le pipeline de complément est le chemin d’accès des segments de pipeline que l’application hôte et son complément doivent utiliser pour communiquer entre eux.</span><span class="sxs-lookup"><span data-stu-id="fb677-103">The add-in pipeline is the path of pipeline segments that the host application and its add-in must use to communicate with each other.</span></span>  
  
 <span data-ttu-id="fb677-104">L’illustration suivante montre le pipeline de communication et ses segments.</span><span class="sxs-lookup"><span data-stu-id="fb677-104">The following illustration shows the communication pipeline and its segments.</span></span>  
  
 <span data-ttu-id="fb677-105">![Ajouter &#45; dans le modèle de pipeline. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="fb677-105">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="fb677-106">Pipeline de complément</span><span class="sxs-lookup"><span data-stu-id="fb677-106">Add-in pipeline</span></span>  
  
 <span data-ttu-id="fb677-107">L’application hôte est à une extrémité du pipeline et le complément est à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="fb677-107">The host application is at one end of the pipeline and the add-in is at the other end.</span></span> <span data-ttu-id="fb677-108">À partir de chaque extrémité et le déplacement vers le milieu, l’application hôte et le complément ont une classe de base abstraite qui définit une vue du modèle d’objet qu’ils partagent.</span><span class="sxs-lookup"><span data-stu-id="fb677-108">Starting from each end and moving toward the middle, both the host application and the add-in have an abstract base class that defines a view of the object model that they both share.</span></span> <span data-ttu-id="fb677-109">Ces types (classes) constituent le segment de pipeline de complément, la vue et la vue hôte du segment de pipeline de complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-109">These types (classes) make up the add-in view pipeline segment and the host view of the add-in pipeline segment.</span></span> <span data-ttu-id="fb677-110">Le segment de pipeline de complément, la vue contient souvent plus d’une classe abstraite, mais la classe héritant de la macro complémentaire est connue en tant que la base de complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-110">The add-in view pipeline segment often contains more than one abstract class but the class that the add-in inherits from is known as the add-in base.</span></span>  
  
 <span data-ttu-id="fb677-111">Le segment de pipeline adaptateur côté complément et la conversion de segment de pipeline adaptateur côté hôte le flux de types entre leurs segments de pipeline de vue et le segment de pipeline du contrat.</span><span class="sxs-lookup"><span data-stu-id="fb677-111">The add-in-side adapter pipeline segment and the host-side adapter pipeline segment convert the flow of types between their view pipeline segments and the contract pipeline segment.</span></span> <span data-ttu-id="fb677-112">Le segment central du pipeline est un contrat qui est dérivé de la <xref:System.AddIn.Contract.IContract> interface.</span><span class="sxs-lookup"><span data-stu-id="fb677-112">The central segment of the pipeline is a contract that is derived from the <xref:System.AddIn.Contract.IContract> interface.</span></span> <span data-ttu-id="fb677-113">Ce contrat définit les méthodes que l’application hôte et son complément utiliseront.</span><span class="sxs-lookup"><span data-stu-id="fb677-113">This contract defines the methods that the host application and its add-in will both use.</span></span>  
  
 <span data-ttu-id="fb677-114">Si vous chargez l’hôte et le complément dans des domaines d’application distincts, vous avez une limite d’isolation qui sépare la portée de l’application hôte à partir de l’étendue de la macro complémentaire.</span><span class="sxs-lookup"><span data-stu-id="fb677-114">If you load the host and the add-in into separate application domains, you have an isolation boundary that separates the scope of the host application from the scope of the add-in.</span></span> <span data-ttu-id="fb677-115">Le contrat est le seul assembly est chargé dans l’hôte et les domaines d’application du complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-115">The contract is the only assembly that is loaded in both the host and add-in application domains.</span></span> <span data-ttu-id="fb677-116">L’ordinateur hôte et le complément chaque font référence uniquement à leur vue des méthodes de contrat.</span><span class="sxs-lookup"><span data-stu-id="fb677-116">The host and the add-in each refer only to their view of the contract methods.</span></span> <span data-ttu-id="fb677-117">Par conséquent, ils sont séparés par une couche d’abstraction du contrat.</span><span class="sxs-lookup"><span data-stu-id="fb677-117">Therefore, they are separated by a layer of abstraction from the contract.</span></span>  
  
 <span data-ttu-id="fb677-118">Pour développer des segments de pipeline, vous devez créer une structure de répertoires qui les contiennent.</span><span class="sxs-lookup"><span data-stu-id="fb677-118">To develop pipeline segments, you must create a directory structure that will contain them.</span></span> <span data-ttu-id="fb677-119">Pour plus d’informations sur les spécifications de développement et les indications de portée, consultez [les exigences de développement de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="fb677-119">For more information about development requirements and scope guidelines, see [Pipeline Development Requirements](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
 <span data-ttu-id="fb677-120">L’illustration suivante montre les types qui composent les segments de pipeline.</span><span class="sxs-lookup"><span data-stu-id="fb677-120">The following illustration shows the types that make up the pipeline segments.</span></span> <span data-ttu-id="fb677-121">Les noms des types indiqués dans l’illustration sont arbitraires, mais tous les types à l’exception de l’hôte et l’ordinateur hôte permet d’afficher les attributs du complément, requièrent afin qu’ils puissent être détectés par les méthodes qui génèrent une banque d’informations.</span><span class="sxs-lookup"><span data-stu-id="fb677-121">The names of the types shown in the illustration are arbitrary, but all types except for the host and the host view of the add-in require attributes so they can be discovered by methods that construct an information store.</span></span>  
  
 <span data-ttu-id="fb677-122">![Ajouter &#45; dans le modèle avec des attributs requis sur les types. ] (../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")</span><span class="sxs-lookup"><span data-stu-id="fb677-122">![Add&#45;in model with required attributes on types.](../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")</span></span>  
<span data-ttu-id="fb677-123">Pipeline de complément avec types</span><span class="sxs-lookup"><span data-stu-id="fb677-123">Add-in pipeline with types</span></span>  
  
 <span data-ttu-id="fb677-124">Le tableau suivant décrit les segments de pipeline pour l’activation d’un complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-124">The following table describes the pipeline segments for activating an add-in.</span></span> <span data-ttu-id="fb677-125">Pour plus d’informations sur ces segments, consultez [contrats, les vues et les adaptateurs](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c).</span><span class="sxs-lookup"><span data-stu-id="fb677-125">For more information about these segments, see [Contracts, Views, and Adapters](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c).</span></span>  
  
|<span data-ttu-id="fb677-126">Segment de pipeline</span><span class="sxs-lookup"><span data-stu-id="fb677-126">Pipeline segment</span></span>|<span data-ttu-id="fb677-127">Description</span><span class="sxs-lookup"><span data-stu-id="fb677-127">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="fb677-128">Host</span><span class="sxs-lookup"><span data-stu-id="fb677-128">Host</span></span>|<span data-ttu-id="fb677-129">L’assembly d’application qui crée une instance d’un complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-129">The application assembly that creates an instance of an add-in.</span></span>|  
|<span data-ttu-id="fb677-130">Vue hôte du complément</span><span class="sxs-lookup"><span data-stu-id="fb677-130">Host view of the add-in</span></span>|<span data-ttu-id="fb677-131">Représente l’affichage de l’application hôte des types d’objets et méthodes utilisés pour communiquer avec le complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-131">Represents the host application's view of the object types and methods used to communicate with the add-in.</span></span> <span data-ttu-id="fb677-132">La vue hôte est une interface ou une classe de base abstraite.</span><span class="sxs-lookup"><span data-stu-id="fb677-132">The host view is an abstract base class or interface.</span></span>|  
|<span data-ttu-id="fb677-133">Adaptateur côté hôte</span><span class="sxs-lookup"><span data-stu-id="fb677-133">Host-side adapter</span></span>|<span data-ttu-id="fb677-134">Un assembly avec une ou plusieurs classes qui adapte des méthodes vers et depuis le contrat.</span><span class="sxs-lookup"><span data-stu-id="fb677-134">An assembly with one or more classes that adapts methods to and from the contract.</span></span><br /><br /> <span data-ttu-id="fb677-135">Ce segment de pipeline est identifié à l’aide de la <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="fb677-135">This pipeline segment is identified by using the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute.</span></span><br /><br /> <span data-ttu-id="fb677-136">Les assemblys composés de plusieurs modules ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fb677-136">Multi-module assemblies are not supported.</span></span>|  
|<span data-ttu-id="fb677-137">Contrat</span><span class="sxs-lookup"><span data-stu-id="fb677-137">Contract</span></span>|<span data-ttu-id="fb677-138">Une interface qui est dérivée de la <xref:System.AddIn.Contract.IContract> interface et qui définit le protocole pour communiquer des types entre l’hôte et son complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-138">An interface that is derived from the <xref:System.AddIn.Contract.IContract> interface and that defines the protocol for communicating types between the host and its add-in.</span></span><br /><br /> <span data-ttu-id="fb677-139">Ce segment de pipeline est identifié en définissant le <xref:System.AddIn.Pipeline.AddInContractAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="fb677-139">This pipeline segment is identified by setting the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>|  
|<span data-ttu-id="fb677-140">Adaptateur côté complément</span><span class="sxs-lookup"><span data-stu-id="fb677-140">Add-in-side adapter</span></span>|<span data-ttu-id="fb677-141">Un assembly avec une ou plusieurs classes qui adapte des méthodes vers et depuis le contrat.</span><span class="sxs-lookup"><span data-stu-id="fb677-141">An assembly with one or more classes that adapts methods to and from the contract.</span></span><br /><br /> <span data-ttu-id="fb677-142">Ce segment de pipeline est identifié à l’aide de la <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="fb677-142">This pipeline segment is identified by using the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute.</span></span><br /><br /> <span data-ttu-id="fb677-143">Chaque assembly dans le répertoire de l’adaptateur côté complément qui contient un type qui a un <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribut est chargé dans domaine d’application du complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-143">Each assembly in the add-in-side adapter directory that contains a type that has an <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute is loaded into the add-in's application domain.</span></span><br /><br /> <span data-ttu-id="fb677-144">Chaque assembly dans le répertoire côté complément est chargé dans son propre domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="fb677-144">Each assembly in the add-in-side directory is loaded in its own application domain.</span></span><br /><br /> <span data-ttu-id="fb677-145">Les assemblys composés de plusieurs modules ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fb677-145">Multi-module assemblies are not supported</span></span>|  
|<span data-ttu-id="fb677-146">Vue complément</span><span class="sxs-lookup"><span data-stu-id="fb677-146">Add-in view</span></span>|<span data-ttu-id="fb677-147">Un assembly qui représente la vue du complément des types d’objets et les méthodes utilisées pour communiquer avec l’hôte.</span><span class="sxs-lookup"><span data-stu-id="fb677-147">An assembly that represents the add-in's view of the object types and methods that are used to communicate with the host.</span></span> <span data-ttu-id="fb677-148">La vue du complément est une interface ou une classe de base abstraite.</span><span class="sxs-lookup"><span data-stu-id="fb677-148">The add-in view is an abstract base class or interface.</span></span><br /><br /> <span data-ttu-id="fb677-149">Ce segment de pipeline est identifié à l’aide de la <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="fb677-149">This pipeline segment is identified by using the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span><br /><br /> <span data-ttu-id="fb677-150">Chaque assembly du répertoire AddInViews qui contient un type qui a un <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribut est chargé dans domaine d’application du complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-150">Each assembly in the AddInViews directory that contains a type that has an <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute is loaded into the add-in's application domain.</span></span>|  
|<span data-ttu-id="fb677-151">Complément</span><span class="sxs-lookup"><span data-stu-id="fb677-151">Add-in</span></span>|<span data-ttu-id="fb677-152">Un type instancié qui exécute un service pour l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="fb677-152">An instantiated type that performs a service for the host.</span></span>|  
  
## <a name="pipeline-activation-path"></a><span data-ttu-id="fb677-153">Chemin d’Activation du pipeline</span><span class="sxs-lookup"><span data-stu-id="fb677-153">Pipeline Activation Path</span></span>  
 <span data-ttu-id="fb677-154">L’illustration suivante montre l’activation de types lorsqu’un complément est activé.</span><span class="sxs-lookup"><span data-stu-id="fb677-154">The following illustration shows the activation of types when an add-in is activated.</span></span> <span data-ttu-id="fb677-155">Il montre également le passage d’objets à l’hôte, telles que les résultats d’un calcul ou une collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="fb677-155">It also shows the passing of objects to the host, such as the results of a calculation or a collection of objects.</span></span> <span data-ttu-id="fb677-156">Il s’agit du scénario le plus courant.</span><span class="sxs-lookup"><span data-stu-id="fb677-156">This is the most typical scenario.</span></span>  
  
 <span data-ttu-id="fb677-157">![Ajouter &#45; dans le modèle avec le chemin d’accès d’activation. ] (../../../docs/framework/add-ins/media/addin6.png "AddIn6")</span><span class="sxs-lookup"><span data-stu-id="fb677-157">![Add&#45;in model with activation path.](../../../docs/framework/add-ins/media/addin6.png "AddIn6")</span></span>  
<span data-ttu-id="fb677-158">Chemin d’activation du complément à l’hôte</span><span class="sxs-lookup"><span data-stu-id="fb677-158">Activation path from the add-in to the host</span></span>  
  
 <span data-ttu-id="fb677-159">Le chemin d’accès de l’activation du pipeline se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="fb677-159">The activation path of the pipeline occurs as follows:</span></span>  
  
1.  <span data-ttu-id="fb677-160">L’application hôte Active le complément avec le <xref:System.AddIn.Hosting.AddInToken.Activate%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="fb677-160">The host application activates the add-in with the <xref:System.AddIn.Hosting.AddInToken.Activate%2A> method.</span></span>  
  
2.  <span data-ttu-id="fb677-161">La vue du complément, complément, adaptateur côté complément et les assemblys de contrat sont chargés dans domaine d’application du complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-161">The add-in, add-in view, add-in-side adapter, and the contract assemblies are loaded into the add-in's application domain.</span></span>  
  
3.  <span data-ttu-id="fb677-162">Une instance de l’adaptateur côté complément est créée à l’aide de la vue de complément (avec la classe identifiée par le <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribut) en tant que son constructeur.</span><span class="sxs-lookup"><span data-stu-id="fb677-162">An instance of the add-in-side adapter is created using the add-in view (with the class identified by the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute) as its constructor.</span></span> <span data-ttu-id="fb677-163">L’adaptateur côté complément hérite du contrat.</span><span class="sxs-lookup"><span data-stu-id="fb677-163">The add-in-side adapter inherits from the contract.</span></span>  
  
4.  <span data-ttu-id="fb677-164">L’adaptateur côté complément, qui est typée en tant que le contrat, est passé au constructeur de l’adaptateur côté hôte au-delà des limites d’isolement (facultatif).</span><span class="sxs-lookup"><span data-stu-id="fb677-164">The add-in-side adapter, which is typed as the contract, is passed across the (optional) isolation boundary to the host-side adapter's constructor.</span></span>  
  
5.  <span data-ttu-id="fb677-165">La vue de l’hôte de l’adaptateur de complément, côté hôte et les assemblys de contrat sont chargés dans le domaine d’application de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="fb677-165">The host view of the add-in, host-side adapter, and the contract assemblies are loaded into the host's application domain.</span></span>  
  
6.  <span data-ttu-id="fb677-166">Une instance de l’adaptateur côté hôte est créée à l’aide du contrat comme son constructeur.</span><span class="sxs-lookup"><span data-stu-id="fb677-166">An instance of the host-side adapter is created using the contract as its constructor.</span></span> <span data-ttu-id="fb677-167">L’adaptateur côté hôte hérite de la vue hôte du complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-167">The host-side adapter inherits from the host view of the add-in.</span></span>  
  
7.  <span data-ttu-id="fb677-168">L’hôte possède le complément, ce qui est de type comme afficher de l’ajout de l’hôte et peut continuer à appeler ses méthodes.</span><span class="sxs-lookup"><span data-stu-id="fb677-168">The host has the add-in, which is typed as the host view of the add-in, and can continue calling its methods.</span></span>  
  
## <a name="walkthroughs"></a><span data-ttu-id="fb677-169">Procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="fb677-169">Walkthroughs</span></span>  
 <span data-ttu-id="fb677-170">Il existe trois rubriques de procédure pas à pas qui décrivent comment créer des pipelines à l’aide de Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="fb677-170">There are three walkthrough topics that describe how to create pipelines using Visual Studio:</span></span>  
  
-   [<span data-ttu-id="fb677-171">Procédure pas à pas : Création d’une Application Extensible</span><span class="sxs-lookup"><span data-stu-id="fb677-171">Walkthrough: Creating an Extensible Application</span></span>](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     <span data-ttu-id="fb677-172">Décrit un complément calculatrice qui effectue l’addition, soustraction, multiplication et calculs de division pour l’hôte.</span><span class="sxs-lookup"><span data-stu-id="fb677-172">Describes a calculator add-in that performs addition, subtraction, multiplication, and divsion calculations for the host.</span></span>  
  
-   [<span data-ttu-id="fb677-173">Procédure pas à pas : L’activation de la compatibilité descendante lorsque votre hôte change</span><span class="sxs-lookup"><span data-stu-id="fb677-173">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     <span data-ttu-id="fb677-174">Décrit un complément de calculatrice avec des fonctions de calcul améliorées et comment assurer la compatibilité avec le premier calcul complément.</span><span class="sxs-lookup"><span data-stu-id="fb677-174">Describes a calculator add-in with enhanced calculation capabilities, and how to maintain compatibility with the first calculator add-in.</span></span>  
  
-   [<span data-ttu-id="fb677-175">Procédure pas à pas : Passage de Collections entre les hôtes et les compléments</span><span class="sxs-lookup"><span data-stu-id="fb677-175">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     <span data-ttu-id="fb677-176">Explique comment passer des collections de données sur le pipeline à l’aide d’un scénario de librairie.</span><span class="sxs-lookup"><span data-stu-id="fb677-176">Describes how to pass data collections over the pipeline using a book store scenario.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb677-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb677-177">See Also</span></span>  
 [<span data-ttu-id="fb677-178">Scénarios de Pipeline de complément</span><span class="sxs-lookup"><span data-stu-id="fb677-178">Add-in Pipeline Scenarios</span></span>](http://msdn.microsoft.com/en-us/feb70e0b-8734-494c-aeaf-b567f014043e)  
 [<span data-ttu-id="fb677-179">Compléments et extensibilité</span><span class="sxs-lookup"><span data-stu-id="fb677-179">Add-ins and Extensibility</span></span>](../../../docs/framework/add-ins/index.md)