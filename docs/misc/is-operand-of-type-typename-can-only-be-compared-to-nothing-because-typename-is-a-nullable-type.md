---
title: "&#39;typename&#39; は Null 許容型であるため、型 &#39;typename&#39; の &#39;Is&#39; オペランドは &#39;Nothing&#39; とのみ比較できます | Microsoft Docs"
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
  - "vbc32127"
  - "bc32127"
helpviewer_keywords: 
  - "BC32127"
ms.assetid: 68b745b5-8605-4bf3-a6ec-69e67b3cff2d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;typename&#39; は Null 許容型であるため、型 &#39;typename&#39; の &#39;Is&#39; オペランドは &#39;Nothing&#39; とのみ比較できます
Null 許容型として宣言された変数が、`Is` 演算子を使用して、`Nothing` 以外の式と比較されました。  
  
 **エラー ID:** BC32127  
  
### このエラーを解決するには  
  
1.  `Is` 演算子を使用して、Null 許容型を `Nothing` 以外の式と比較するには、次の例に示すように、Null 許容型に対して `GetType` メソッドを呼び出し、その結果を式と比較します。  
  
    ```vb#  
    Dim number? As Integer = 5 If number IsNot Nothing Then If number.GetType() Is Type.GetType("System.Int32") Then End If End If  
    ```  
  
## 参照  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Is Operator](/dotnet/visual-basic/language-reference/operators/is-operator)