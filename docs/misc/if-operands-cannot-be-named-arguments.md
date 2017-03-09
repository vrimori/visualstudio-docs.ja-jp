---
title: "&#39;If&#39; オペランドを名前付き引数にすることはできません | Microsoft Docs"
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
  - "bc33105"
  - "vbc33105"
helpviewer_keywords: 
  - "BC33105"
ms.assetid: 596baeb6-a44f-4d92-beb7-06624b60c00d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39; オペランドを名前付き引数にすることはできません
`If` 演算子のオペランドで名前付き引数を使用することは正しくありません。 次の例では、このエラーが発生します。  
  
```  
Dim i As Integer Dim result As String ' Not valid. ' result = (If(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 これは、次のコードに示す名前付き引数を許可する `IIf` 関数とは異なります。  
  
```  
' Valid. IIf(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 **エラー ID:** BC33105  
  
### このエラーを解決するには  
  
-   次のコード例に示すように、オペランドから名前の割り当てを削除します。  
  
    ```  
    result = If(i > 0, "positive", "not positive")  
    ```  
  
## 参照  
 [If Operator](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)