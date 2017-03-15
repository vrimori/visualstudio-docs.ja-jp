---
title: "配列の配列を初期化する場合、トップレベル配列に対してのみ境界を指定できます | Microsoft Docs"
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
  - "bc32014"
  - "vbc32014"
helpviewer_keywords: 
  - "BC32014"
ms.assetid: d8d7155d-82d1-4a25-b9bb-1883e1586383
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 配列の配列を初期化する場合、トップレベル配列に対してのみ境界を指定できます
ジャグ配列 \(配列の配列\) の配列初期化では、いずれかの下位レベルの初期の長さが設定されます。 配列の宣言ステートメントでは、最上位の配列のみの長さを指定できます。  
  
 **エラー ID:** BC32014  
  
### このエラーを解決するには  
  
1.  最上位の配列を除くすべての配列から長さの指定を削除します。  
  
2.  後続の代入ステートメントで `New` キーワードを使用して、下位レベルの配列の初期の長さを設定します。  
  
## 参照  
 [ビルド内にありません: 配列変数](http://msdn.microsoft.com/ja-jp/c2da78bd-6928-46ba-805f-44f819dfaf93)   
 [ビルド内にありません: Visual Basic におけるジャグ配列](http://msdn.microsoft.com/ja-jp/05c12439-ee8f-4fef-ba75-b35402b67ab9)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)