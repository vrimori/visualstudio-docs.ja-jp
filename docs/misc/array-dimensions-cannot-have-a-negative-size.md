---
title: "配列の次元を、負の値のサイズに設定することはできません | Microsoft Docs"
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
  - "bc30611"
  - "vbc30611"
helpviewer_keywords: 
  - "BC30611"
ms.assetid: e310bd0d-f221-4b02-87f3-02124f4de87c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 配列の次元を、負の値のサイズに設定することはできません
指定された 1 つ以上の配列の範囲が負の数値です。 負の数の添字を指定できるのは、空の配列を宣言するために範囲の上限として \-1 を使用する場合のみです。 そのような配列は要素がゼロ個ですが、`Nothing` ではありません。  
  
 **エラー ID:** BC30611  
  
### このエラーを解決するには  
  
-   負の配列の範囲を正の数に置き換えてください。  
  
## 参照  
 [配列](/dotnet/visual-basic/programming-guide/language-features/arrays/index)