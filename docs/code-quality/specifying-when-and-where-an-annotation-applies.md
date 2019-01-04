---
title: 注釈を適用するタイミングと場所の指定
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 4ebdc8592d26c124f98ff9d390e173b6675f09d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863304"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>注釈を適用するタイミングと場所の指定
注釈が条件付きの場合、アナライザーを指定するには、その他の注釈が必要です。  たとえば、関数に同期または非同期にできる変数がある場合、関数は次のましょう。同期の場合は、常に最終的に成功しますが、非同期の場合、エラーを報告場合、それがすぐに成功することはできません。 関数は同期的に呼び出されると、結果の値をチェックはない値をコード アナライザー返されませんが、これはからです。  ただし、関数を非同期的に呼び出すし、関数の結果はチェックされません、重大なエラーが発生する可能性があります。 この例で使用することが状況、`_When_`注釈: この記事の後半で説明されている、チェックを有効にします。

## <a name="structural-annotations"></a>構造的な注釈
 注釈を適用するタイミングと場所を制御するには、次の構造的な注釈を使用します。

|注釈|説明|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` 左辺の値を生成する式です。 注釈`anno-list`によって指定されるオブジェクトに適用される`expr`します。 各注釈で`anno-list`、`expr`で前提条件は、注釈が解釈され、事後条件で事後条件の場合に、注釈が解釈される場合に、前提条件で解釈されます。|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` 左辺の値を生成する式です。 注釈`anno-list`によって指定されるオブジェクトに適用される`expr`します。 各注釈で`anno-list`、`expr`での前提条件で注釈が解釈され、事後条件で事後条件の場合に、注釈が解釈される場合に、前提条件で解釈されます。<br /><br /> `iter` 注釈のスコープ変数の名前を指定します (含まれます`anno-list`)。 `iter` 暗黙の型を持つ`long`します。 評価は、外側のスコープ内の同じ名前の変数は表示されません。<br /><br /> `elem-count` 整数に評価される式です。|
|`_Group_(anno-list)`|注釈`anno-list`はすべてにそれぞれの注釈に適用されるグループの注釈に適用されるすべての修飾子があるとします。|
|`_When_(expr, anno-list)`|`expr` 変換できる式は、`bool`します。 0 以外 (`true`) で指定されている注釈`anno-list`適用可能なと見なされます。<br /><br /> 既定では、各注釈で`anno-list`、`expr`は注釈での前提条件は、出力値を使用する場合と、注釈事後条件である場合は、入力値を使用してとして解釈されます。 既定値を上書きするに使用することができます、`_Old_`組み込みの入力値を使用することを示す事後条件を評価するとき。 **注:** 使用しての結果として異なる注釈が有効になって`_When_`値が変更可能な場合: たとえば、 `*pLength`— が関係しているための評価結果`expr`precondition で事後条件の評価の結果から異なる場合があります。|

## <a name="see-also"></a>関連項目

- [SAL 注釈を使って C/C++ のコード障害を減らす方法](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL について](../code-quality/understanding-sal.md)
- [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)
- [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)
- [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)
- [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)
- [組み込み関数](../code-quality/intrinsic-functions.md)
- [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)