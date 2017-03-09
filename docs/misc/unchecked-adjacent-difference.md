---
title: "unchecked_adjacent_difference | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_adjacent_difference"
  - "std::unchecked_adjacent_difference"
  - "unchecked_adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_adjacent_difference 関数"
ms.assetid: 3a6b0b49-a84b-40b1-bcd5-3bf76c6ef7d7
caps.latest.revision: 14
caps.handback.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_adjacent_difference
同じ [adjacent\_difference](../Topic/adjacent_difference.md), 、出力反復子としてチェックを行わない反復子を使用できますが、ときに \_SECURE\_SCL \= 1 が定義されています。`unchecked_adjacent_difference` 定義された、 `stdext` 名前空間。  
  
> [!NOTE]
>  このアルゴリズムは、標準 C\+\+ ライブラリに対する Microsoft 拡張機能です。 このアルゴリズムを使用して実装されたコードは、移植可能ではありません。  
  
## 構文  
  
```  
template<class InputIterator, class OutIterator>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result   
   );  
  
template<class InputIterator, class OutputIterator, class BinaryOperation>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result,   
      BinaryOperation _Binary_op  
   );  
```  
  
#### パラメーター  
 `_First`  
 含まれる要素がそれぞれの先行要素と差分処理されるか、または値のペアが別の指定された二項演算で処理される入力範囲の先頭の要素を示す入力反復子。  
  
 `_Last`  
 含まれる要素がそれぞれの先行要素と差分処理されるか、または値のペアが別の指定された二項演算で処理される入力範囲の最後の要素を示す入力反復子。  
  
 `_Result`  
 一連の差分または指定された演算の結果が格納されるターゲット範囲の先頭の要素を示す出力反復子。  
  
 `_Binary_op`  
 差分プロシージャの減算演算を置き換える一般的な演算で適用される二項演算。  
  
## 戻り値  
 ターゲット範囲の末尾を示す出力反復子: `_Result` \+ \(`_Last` \- `_First`\)。  
  
## 解説  
 参照してください [adjacent\_difference](../Topic/adjacent_difference.md) 用のコード サンプルです。  
  
 Checked 反復子の詳細については、次を参照してください。 [チェックを行う反復子](/visual-cpp/standard-library/checked-iterators)します。  
  
## 必要条件  
 **ヘッダー:** \<numeric\>  
  
 **名前空間:** stdext  
  
## 参照  
 [標準テンプレート ライブラリ](../misc/standard-template-library.md)