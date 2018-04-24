---
title: 注釈を適用するタイミングと場所の指定
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 288d422de6d4e4c0f372820d838d0173c990f2a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>注釈を適用するタイミングと場所の指定
注釈が条件付きの場合、アナライザーをすることを指定するには、その他の注釈があります。  たとえば、関数が同期または非同期のどちらかにできる変数を持つ場合、関数は次のようにします。 同期の場合、常に最終的に成功しますが、非同期の場合、エラーが報告場合は、すぐには成功ことはできません。 関数は同期的に呼び出されると、結果値をチェックするありません値を提供、コード アナライザーがないが返されたためです。  しかし、関数が非同期的に呼び出すし、関数の結果はチェックされません、重大なエラーが発生する可能性です。 この例で使用する可能性があります、状況、`_When_`注釈 — この記事で後述する — チェックを有効にします。

## <a name="structural-annotations"></a>構造的な注釈
 注釈を適用するタイミングと場所を制御するには、次の構造的な注釈を使用します。

|注釈|説明|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` 左辺の値を生成する式です。 注釈`anno-list`によって指定されるオブジェクトに適用される`expr`です。 各注釈で`anno-list`、`expr`で前提条件は、注釈を解釈し、事後条件では、注釈は事後条件で解釈される場合か、前提条件で解釈されます。|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` 左辺の値を生成する式です。 注釈`anno-list`によって指定されるオブジェクトに適用される`expr`です。 各注釈で`anno-list`、 `expr` precondition で注釈を解釈し、事後条件では、注釈は事後条件で解釈される場合か、前提条件で解釈されます。<br /><br /> `iter` 注釈のスコープである変数の名前を指定します (含まれます`anno-list`)。 `iter` 暗黙の型を持つ`long`します。 評価版から、外側のスコープで同じ名前を持つ変数が非表示になります。<br /><br /> `elem-count` 整数に評価される式です。|
|`_Group_(anno-list)`|注釈`anno-list`をそれぞれの注釈に適用されるグループの注釈に適用されるすべての修飾子を持つと見なさすべてです。|
|`_When_(expr, anno-list)`|`expr` 変換できる式は、`bool`です。 ゼロ以外である場合 (`true`) で指定されている注釈`anno-list`適用できると見なされます。<br /><br /> 既定では、各注釈で`anno-list`、`expr`は、入力値を使用して注釈が、前提条件と場合、出力値を使用して、注釈は事後条件として解釈されます。 既定値を上書きするに使用することができます、`_Old_`組み込みの入力値を使用することを示すために事後条件を評価する際にします。 **注:**異なる注釈を使用した結果として有効にする可能性があります`_When_`値が変更可能な場合 — たとえば、 `*pLength`— が関係しているための評価結果`expr`事前条件では、その評価からで異なる場合があります事後条件で発生します。|

## <a name="see-also"></a>関連項目
 [SAL 注釈を使用して C/C++ のコード障害を減らす](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [SAL を理解する](../code-quality/understanding-sal.md)[関数パラメーターおよび戻り値の注釈を付ける](../code-quality/annotating-function-parameters-and-return-values.md) [の関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)[構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)[ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)[の組み込み関数](../code-quality/intrinsic-functions.md)[ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)