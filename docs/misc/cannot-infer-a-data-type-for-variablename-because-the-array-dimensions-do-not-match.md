---
title: "配列の次元が一致しないため、&#39;&lt;variablename&gt;&#39; のデータ型は推論できません | Microsoft Docs"
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
  - "bc36909"
  - "vbc36909"
helpviewer_keywords: 
  - "BC36909"
ms.assetid: e41fec81-efec-4395-a0a5-d81906a2d4f1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 配列の次元が一致しないため、&#39;&lt;variablename&gt;&#39; のデータ型は推論できません
配列を初期化するために使用される次元が、宣言内の次元と一致しない場合、コンパイラは、配列のデータ型を推論できません。 たとえば、次のコードでは、このエラーが発生します。  
  
```vb#  
' Valid. exampleArray1 is a one-dimensional array of integers. Dim exampleArray1() = New Integer() {1, 2, 3} ' Not valid. 'Dim exampleArray2(,) = New Integer() {1, 2, 3} 'Dim exampleArray3(,) = New Integer() {}  
```  
  
 **エラー ID:** BC36909  
  
## 参照  
 [Local Type Inference](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [NOTINBUILD 方法: 多次元配列を初期化する](http://msdn.microsoft.com/ja-jp/502dcf8b-d86c-46f1-ad7d-3ce809645774)