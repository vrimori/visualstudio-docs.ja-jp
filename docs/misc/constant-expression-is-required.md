---
title: "定数式が必要です | Microsoft Docs"
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
  - "bc30059"
  - "vbc30059"
helpviewer_keywords: 
  - "BC30059"
ms.assetid: fdd5e7bb-6370-4a63-bbb6-23b15badb4c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 定数式が必要です
`Const` ステートメントが定数を正しく初期化していないか、または配列の宣言が変数を使用して要素の数を指定しています。  
  
 **エラー ID:** BC30059  
  
### このエラーを解決するには  
  
1.  宣言が `Const` ステートメントである場合、定数が、リテラル、以前に宣言された定数、列挙体のメンバーによって初期化されるか、または演算子と組み合わせた、リテラル、定数、列挙型メンバーの組み合わせによって初期化されることを確認します。  
  
2.  宣言が配列を指定する場合は、要素の数を指定するために変数が使用されているかどうかを確認します。 使用されている場合は、変数を定数式に置き換えます。  
  
## 参照  
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [ビルド内にありません: 配列変数](http://msdn.microsoft.com/ja-jp/c2da78bd-6928-46ba-805f-44f819dfaf93)