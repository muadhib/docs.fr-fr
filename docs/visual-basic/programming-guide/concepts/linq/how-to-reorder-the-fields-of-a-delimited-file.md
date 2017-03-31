---
title: "Comment : réorganiser les champs d’un fichier délimité (LINQ) (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9abb0510ed3944cd80d6658238ef79d64dc0ca27
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>Comment : réorganiser les champs d’un fichier délimité (LINQ) (Visual Basic)
Un fichier de valeurs séparées par des virgules (CSV) est un fichier texte qui est souvent utilisé pour stocker les données de feuille de calcul ou d’autres données tabulaires qui sont représentées par des lignes et des colonnes. À l’aide de la <xref:System.String.Split%2A>méthode pour séparer les champs, il est très facile d’interroger et manipuler des fichiers CSV à l’aide de LINQ.</xref:System.String.Split%2A> En fait, la même technique peut servir à réorganiser les parties de n’importe quelle ligne structurée de texte. Il n’est pas limitée aux fichiers CSV.  
  
 Dans l’exemple suivant, supposons que les trois colonnes représentent « last name, » des étudiants « first name » et « ID ». Les champs sont dans l’ordre alphabétique selon les noms des étudiants. La requête produit une séquence dans laquelle la colonne ID apparaît en premier, suivie d’une deuxième colonne qui associe le prénom et le nom de l’étudiant. Les lignes sont réorganisées d’après le champ ID. Les résultats sont enregistrés dans un nouveau fichier et les données d’origine ne sont pas modifiées.  
  
### <a name="to-create-the-data-file"></a>Pour créer le fichier de données  
  
1.  Copiez les lignes suivantes dans un fichier texte brut nommé spreadsheet1.csv. Enregistrez le fichier dans votre dossier de projet.  
  
    ```  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a>Exemple  
  
```vb  
Class CSVFiles  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data source.  
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")  
  
        ' Execute the query. Put field 2 first, then  
        ' reverse and combine fields 0 and 1 from the old field  
        Dim lineQuery = From line In lines   
                        Let x = line.Split(New Char() {","})   
                        Order By x(2)   
                        Select x(2) & ", " & (x(1) & " " & x(0))  
  
        ' Execute the query and write out the new file. Note that WriteAllLines  
        ' takes a string array, so ToArray is called on the query.  
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output to spreadsheet2.csv:  
' 111, Svetlana Omelchenko  
' 112, Claire O'Donnell  
' 113, Sven Mortensen  
' 114, Cesar Garcia  
' 115, Debra Garcia  
' 116, Fadi Fakhouri  
' 117, Hanying Feng  
' 118, Hugo Garcia  
' 119, Lance Tucker  
' 120, Terry Adams  
' 121, Eugene Zabokritski  
' 122, Michael Tucker  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [LINQ et répertoires de fichiers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)   
 [Guide pratique : générer du code XML à partir de fichiers CSV](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)