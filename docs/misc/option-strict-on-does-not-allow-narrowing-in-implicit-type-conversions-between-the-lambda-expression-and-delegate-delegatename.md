---
title: "Option Strict On では、ラムダ式とデリゲート &#39;&lt;delegatename&gt;&#39; の間の暗黙的な型変換で縮小変換を許可していません | Microsoft Docs"
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
  - "bc36662"
  - "vbc36662"
helpviewer_keywords: 
  - "BC36662"
ms.assetid: 4504497b-56ba-4631-ad7b-59975f7fee04
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、ラムダ式とデリゲート &#39;&lt;delegatename&gt;&#39; の間の暗黙的な型変換で縮小変換を許可していません
`Option Strict` がオンの場合、デリゲート内のパラメーターのデータ型と、そのデリゲート型の変数に割り当てられているラムダ式の対応するパラメーターの間で縮小変換を行うことはできません。 たとえば、次のコードでは、デリゲート `Del` に型 `Integer` の 1 つのパラメーターがあります。  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String  
```  
  
 そのため、型 `Del` の変数に割り当てられているラムダ式の対応するパラメーターは、`Integer`、または `Integer` からの拡大変換が存在する任意のデータ型でなければなりません。  
  
```vb#  
' Valid. Dim example1 As Del = Function(n As Integer) "Valid" Dim example2 As Del = Function(n As Long) "Valid" ' Not valid. Dim example3 As Del = Function(n As Short) "Not Valid"  
```  
  
 **エラー ID:** BC36662  
  
### このエラーを解決するには  
  
-   デリゲートまたはラムダ式のパラメーターのデータ型を変更して、必要な拡大関係が存在するようにします。  
  
-   ラムダ式でパラメーターのデータ型を指定しません。 型は、デリゲートの対応するパラメーターから推定されます。  
  
    ```vb#  
    Dim example4 As Del = Function(n) "Valid"  
    ```  
  
## 参照  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Delegates](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)