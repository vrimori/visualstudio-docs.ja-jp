---
title: "Option Strict On では、各ラムダ式のパラメーターの型を推論できない場合、そのパラメーターを &#39;As&#39; 句で宣言する必要があります。 | Microsoft Docs"
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
  - "bc36642"
  - "vbc36642"
helpviewer_keywords: 
  - "BC36642"
ms.assetid: 2aaa62b8-49c9-4ae8-b0f5-08e3f0b5ad10
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、各ラムダ式のパラメーターの型を推論できない場合、そのパラメーターを &#39;As&#39; 句で宣言する必要があります。
ラムダ式で `As` 句を使用せずにパラメーター宣言し、`Option Strict` がオンになっています。  
  
```  
' Not valid when Option Strict is on. ' Dim increment1 = Function (n) n + 1  
```  
  
 `n` の型が推論できる場合、前の宣言は有効です。 たとえば、前のラムダ式を関数デリゲート `Del` に割り当てられる場合があります。  
  
```  
Delegate Function Del(ByVal p As Integer) As Integer  
```  
  
 `n` の型はパラメーター `p` から推測できます。  
  
```  
Dim increment2 as Del = Function(n) n + 1  
```  
  
 **エラー ID:** BC36642  
  
### このエラーを解決するには  
  
-   `As` 句をパラメーター宣言に追加します。  
  
    ```  
    Dim increment3 = Function (n As Integer) n + 1  
    ```  
  
## 参照  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)