---
title: "&#39;As New&#39; を含む変数宣言で、Null 許容修飾子を指定することはできません | Microsoft Docs"
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
  - "bc33109"
  - "vbc33109"
helpviewer_keywords: 
  - "BC33109"
ms.assetid: 135def20-3535-4239-bffb-43208d1b3f63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;As New&#39; を含む変数宣言で、Null 許容修飾子を指定することはできません
`As New` が指定されている変数宣言に Null 許容型修飾子 \(?\) が含まれています。 次の例では、このエラーが発生します。  
  
```vb#  
Dim num? As New ExampleStructure  
```  
  
 **エラー ID:** BC33109  
  
### このエラーを解決するには  
  
1.  次の例に示すように、Null 許容型変数宣言から `New` キーワードを削除します。  
  
    ```vb#  
    Dim num? As ExampleStructure  
    ```  
  
## 参照  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)