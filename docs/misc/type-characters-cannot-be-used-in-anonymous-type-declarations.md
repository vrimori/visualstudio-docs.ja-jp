---
title: "型文字を匿名型の宣言で使用することはできません | Microsoft Docs"
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
  - "bc36560"
  - "vbc36560"
helpviewer_keywords: 
  - "BC36560"
ms.assetid: 70eee559-d6fc-409b-b835-2c84511b160e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型文字を匿名型の宣言で使用することはできません
匿名型のインスタンスを宣言するときは、プロパティ名で型文字を使用できません。 プロパティのデータ型は、それに割り当てられた値から推論されます。 たとえば、次の宣言は無効です。  
  
```vb#  
'' Not valid. 'Dim anon1 = New With {.ID$ = "abc"} 'Dim anon2 = New With {.ID$ = 42}  
```  
  
 **エラー ID:** BC36560  
  
### このエラーを解決するには  
  
-   初期化子リストから型文字を削除します。 割り当てられた値は、プロパティのデータ型を設定するために必要な場合は明示的に変換できます。  
  
    ```vb#  
    ' Valid. Dim anon1 = New With {.ID = "abc"} Dim anon2 = New With {.ID = CStr(42)}  
    ```  
  
## 参照  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)