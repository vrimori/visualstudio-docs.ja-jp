---
title: "&#39;Sub New&#39; をインターフェイスで宣言することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30363"
  - "vbc30363"
helpviewer_keywords: 
  - "BC30363"
ms.assetid: 371d9aa8-a935-48ce-ada2-0a69ba20e070
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; をインターフェイスで宣言することはできません
インターフェイスの中で `Sub New` を宣言しようとしました。 コンストラクターであるため、`Sub New` はクラスの作成時に 1 回だけ実行できます。 同じクラスまたは派生クラスの別のコンストラクターで、コード行の先頭に記述して呼び出す以外に明示的に呼び出すことはできません。  
  
 **エラー ID:** BC30363  
  
### このエラーを解決するには  
  
-   `Sub New` を削除するか、コード内のより適切な場所に移動します。  
  
## 参照  
 [ビルド内にありません: コンストラクタとデストラクタの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)