---
title: "注釈を適用するタイミングと場所の指定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Group_"
  - "_At_"
  - "_When_"
  - "_At_buffer_"
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 注釈を適用するタイミングと場所の指定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

注釈は、条件の場合、他の注釈がアナライザーに指定する必要がある場合があります。たとえば、関数に同期または非同期な変数がある関数は次のように動作します。: 同期ケースでは、常に最終的に成功しますが、非同期ケースですぐに成功できない場合、エラーが報告されます。  関数が同期的に呼び出されると、結果値をチェックすると、コードに戻らなかろうアナライザー、値は用意されていません。ただし、関数が非同期的に呼び出され、関数の結果がオンになっていない場合、深刻なエラーが発生することがあります。  この例では、"有効チェックにこの記事の後半で説明する `_When_` 注釈を使用できる状況を示しています。  
  
## 構造的な注釈  
 注釈は、いつどこで発生するかを制御するには、次の構造的な注釈を使用します。  
  
|注釈|説明|  
|--------|--------|  
|`_At_(expr, anno-list)`|`expr` は 左辺値を表す式です。  `anno-list` の注釈は `expr`によって指定されるオブジェクトに適用されます。  `anno-list`の各注釈では、`expr` で注釈が後条件に解釈する注釈が事前条件で解釈されると後条件解釈事前条件。|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` は 左辺値を表す式です。  `anno-list` の注釈は `expr`によって指定されるオブジェクトに適用されます。  `anno-list`の各注釈では、`expr` で注釈が後条件に解釈する注釈が事前条件で解釈されると後条件解釈事前条件。<br /><br /> `iter` は 注釈にスコープ変数の名前です \(`anno-list`の包括\)。  `iter` に 暗黙の型 `long`があります。  任意の外側のスコープ内で、同じ名前の変数が評価になっています。<br /><br /> `elem-count` が整数型に評価される式です。|  
|`_Group_(anno-list)`|`anno-list` の注釈はすべて、注釈に適用されるグループの注釈に適用する修飾子があると見なされます。|  
|`_When_(expr, anno-list)`|`expr` は `bool`に変換できる式です。  これがゼロ以外`true` \(\) は、`anno-list` で考慮する、指定したコメント。<br /><br /> `anno-list`の各注釈の既定では、入力値を使用するように、`expr` 注釈が後条件で注釈が事前条件は、出力値を使用するように解釈されます。  入力値が使用されることを示すために後条件を評価するときに既定の名前をオーバーライドするには、`_Old_` の組み込みを使用できます。 **Note:**  さまざまな注釈は `_When_` の結果としての値の変更、`*pLength`可能になる可能性があります。`expr` の事前条件の評価結果が後条件の評価結果が異なる場合があるため、複雑です。|  
  
## 参照  
 [SAL 注釈を使って C\/C\+\+ のコード障害を減らす方法](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [組み込み関数](../code-quality/intrinsic-functions.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)