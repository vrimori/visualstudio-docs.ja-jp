---
title: "配列修飾子はラムダ式のパラメーター名で指定することはできません。その型でのみ指定できます | Microsoft Docs"
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
  - "vbc36643"
  - "bc36643"
helpviewer_keywords: 
  - "BC36643"
ms.assetid: 34b6141b-6eab-4641-a3f4-53ef28c1792b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 配列修飾子はラムダ式のパラメーター名で指定することはできません。その型でのみ指定できます
ラムダ式には配列引数を渡すことができますが、パラメーター宣言に要素の型を含める必要があります。  
  
```vb#  
' Not valid.  
' Dim arrayExample1 = Function(arrayPara()) 2  
  
' Valid.  
Dim arrayExample2 = Function(arrayPara() As Integer) arrayPara.Length > 0  
Dim arrayexample3 = Function(arrayPara As Integer()) arrayPara.Length > 0  
```  
  
 **エラー ID:** BC36643  
  
### このエラーを解決するには  
  
-   配列パラメーターで要素の型を指定します。  
  
## 参照  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)