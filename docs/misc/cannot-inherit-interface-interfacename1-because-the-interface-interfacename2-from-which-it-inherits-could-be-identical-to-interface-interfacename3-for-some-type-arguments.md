---
title: "継承元のインターフェイス &#39;&#39;&lt;interfacename2&gt;&#39; がインターフェイス &#39;&lt;interfacename3&gt;&#39; と、いくつかの型引数において同一である可能性があるため、インターフェイス &#39;&lt;interfacename1&gt;&#39; を継承できません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32121"
  - "vbc32121"
helpviewer_keywords: 
  - "BC32121"
ms.assetid: 56b1167e-f626-4a27-8395-9d396cc209f2
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 継承元のインターフェイス &#39;&#39;&lt;interfacename2&gt;&#39; がインターフェイス &#39;&lt;interfacename3&gt;&#39; と、いくつかの型引数において同一である可能性があるため、インターフェイス &#39;&lt;interfacename1&gt;&#39; を継承できません
ジェネリック インターフェイスが 2 つ以上のジェネリック インターフェイスから継承されており、その継承のうちの 2 つが、型引数の特定の値について競合している可能性があります。  
  
 次のステートメントでは、このエラーが生成される可能性があります。  
  
```  
Public Interface interfaceA(Of u) Inherits interfaceX(Of u) End Interface Public Interface interfaceX(Of v) End Interface Public Interface derivedInterface(Of t1, t2) Inherits interfaceA(Of t1), interfaceX(Of t2) End Interface  
```  
  
 `derivedInterface` が `t1` と `t2` の両方に同じ型を指定して構築または実装されている場合、同一の型引数を含む 2 つのバージョンの `interfaceX` を継承する必要があります。 この場合、アクセス対象のバージョンがあいまいになる可能性があります。  
  
 **エラー ID:** BC32121  
  
### このエラーを解決するには  
  
-   派生したインターフェイスに指定する型引数の 1 つを変更して、競合を回避します。  
  
     または  
  
-   継承の競合や実装の競合を引き起こす可能性があるインターフェイスの 1 つを、`Inherits` ステートメントから削除します。  
  
## 参照  
 [NOT IN BUILD: インターフェイスの概要](http://msdn.microsoft.com/ja-jp/f96bb470-c1b8-4c73-89bc-6f536b798da1)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)