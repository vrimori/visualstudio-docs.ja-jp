---
title: "型 &#39;&lt;internaltypename&gt;&#39; のアクセスをアセンブリの外部に拡張するため、&#39;&lt;derivedtypename&gt;&#39; は型 &lt;type&gt; &#39;&lt;constructedbasetypename&gt;&#39; から継承できません | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC30922"
  - "vbc30922"
helpviewer_keywords: 
  - "BC30922"
ms.assetid: 81909654-7e67-4b89-81a3-25ae57f678f7
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;internaltypename&gt;&#39; のアクセスをアセンブリの外部に拡張するため、&#39;&lt;derivedtypename&gt;&#39; は型 &lt;type&gt; &#39;&lt;constructedbasetypename&gt;&#39; から継承できません
派生クラスまたはインターフェイスが、基底クラスまたはインターフェイスの型引数として使用することで、制限がある型のアクセス レベルを拡張しようとしています。  
  
 次のコードでは、このエラーが生成される可能性があります。  
  
```  
Public Class baseClass(Of t)  
End Class  
Public Class derivedClass  
    Inherits baseClass(Of restrictedStructure)  
End Class  
Friend Structure restrictedStructure  
    Dim firstMember As Integer  
End Structure  
```  
  
 アセンブリの外部のコードが `restrictedStructure` にアクセスすることはできません。 ただし、`derivedClass` には、それを参照できるすべてのコードからアクセスできます。 そのため、任意のアセンブリのコードに `restrictedStructure` が公開される可能性があるので、`restrictedStructure` を型引数として使用する場合、`derivedClass` は `baseClass` を継承できません。  
  
 **エラー ID:** BC30922  
  
### このエラーを解決するには  
  
-   制限がある型のアクセス レベルを派生型が拡張しないように、クラスまたはインターフェイスのアクセス レベルを調整します。  
  
     または  
  
-   アクセス レベルを調整できない場合、基底クラスまたはインターフェイスを構築するときに、制限がある型を型引数として使用しないでください。  
  
## 参照  
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)