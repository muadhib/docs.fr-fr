---
title: "Guide pratique pour obtenir des informations sur les fichiers, dossiers et lecteurs (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5652dda53a0192ce39be497b6e8ad3c97bef042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Guide pratique pour obtenir des informations sur les fichiers, dossiers et lecteurs (Guide de programmation C#)
Dans le .NET Framework, vous pouvez accéder aux informations sur le système de fichiers en utilisant les classes suivantes :  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 Les classes <xref:System.IO.FileInfo> et <xref:System.IO.DirectoryInfo> représentent un fichier ou un répertoire. Elles contiennent des propriétés qui exposent une grande partie des attributs de fichiers pris en charge par le système de fichiers NTFS. Elles contiennent également des méthodes pour ouvrir, fermer, déplacer et supprimer des fichiers et dossiers. Vous pouvez créer des instances de ces classes en passant une chaîne qui représente le nom du fichier, dossier ou lecteur dans le constructeur :  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Vous pouvez aussi obtenir les noms des fichiers, dossiers ou lecteurs en appelant <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> et <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.  
  
 Les classes <xref:System.IO.Directory?displayProperty=nameWithType> et <xref:System.IO.File?displayProperty=nameWithType> fournissent des méthodes statiques pour récupérer des informations sur les répertoires et les fichiers.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre différentes manières d’accéder aux informations sur les fichiers et dossiers.  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Quand vous traitez des chaînes de chemin spécifiées par l’utilisateur, vous devez également gérer les exceptions dans les cas suivants :  
  
-   Le nom de fichier est mal formé. Par exemple, il contient des caractères non valides ou uniquement des espaces blancs.  
  
-   Le nom de fichier est null.  
  
-   Le nom de fichier est plus long que la longueur maximale définie par le système.  
  
-   Le nom de fichier contient un signe deux-points (:).  
  
 Si l’application ne dispose pas des autorisations suffisantes pour lire le fichier spécifié, la méthode `Exists` retourne `false` indépendamment de l’existence d’un chemin. La méthode ne lève pas d’exception.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO?displayProperty=nameWithType>  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md)
