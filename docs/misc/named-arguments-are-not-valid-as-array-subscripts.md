---
title: "名前付き引数は、配列インデックスとしては有効ではありません | Microsoft Docs"
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
  - "vbc30075"
  - "bc30075"
helpviewer_keywords: 
  - "BC30075"
ms.assetid: a25025c9-0763-4c19-9e9b-cffb9aacaa8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 名前付き引数は、配列インデックスとしては有効ではありません
たとえば `Array(Index := 10)` のように、名前でプロシージャ引数を渡す構文を使用して配列インデックスが指定されています。 この構文は、配列インデックスには無効です。  
  
 **エラー ID:** BC30075  
  
### このエラーを解決するには  
  
-   たとえば `Array(10)` のように、配列インデックスとして通常の変数または定数式を使用します。  
  
## 参照  
 [ビルド内にありません: Visual Basic の配列の概要](http://msdn.microsoft.com/ja-jp/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)