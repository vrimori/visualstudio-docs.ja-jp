---
title: ロック動作に注釈を付ける
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: e8b7aaa9edfeaa2f1515f3fce890c0d7ba9383d2
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804878"
---
# <a name="annotating-locking-behavior"></a>ロック動作に注釈を付ける
マルチ スレッド プログラムでの同時実行のバグを回避するには、以下の適切なロック作業分野と SAL 注釈を使用して常に。

 同時実行のバグが再現、診断、およびは非決定的であるために、デバッグに非常に困難です。 スレッド インタリーブについて推論では、最高では難しく、複数のスレッドがコードの本体を設計するときに非実用的になります。 そのためはマルチ スレッド プログラムでロック規範に従うことをお勧めします。 たとえば、により、デッドロックを回避する、複数のロックの取得中に、ロック順序を無視しない方法について、競合状態を防ぎ、共有リソースにアクセスする前に、適切な guarding ロックを取得します。

 残念ながら、一見単純なロックの規則が驚くほど難しくのプラクティスに従ってください。 今日のプログラミング言語とコンパイラの基本的な制限を直接サポートしていない仕様と要件の同時実行の分析です。 プログラマは、ロックの使用方法について、意図を表現する非公式のコードのコメントに依存する必要があります。

 同時実行 SAL 注釈は、責任、データ後見人立証、ロック順序の階層、およびその他の予期されるロックの動作をロック、ロックの副作用を指定するために設計されています。 暗黙のルールを明示的なことでは、同時実行の SAL 注釈は、コードでロックの規則を使用する方法を文書化するための一貫した方法を提供します。 同時実行の注釈には、競合状態、デッドロック、一致しない同期操作、およびその他の同時実行の微妙なエラーを検索するコード分析ツールの機能も強化します。

## <a name="general-guidelines"></a>一般的なガイドライン
 注釈を使用すると、関数の定義 (呼び出し先) の実装とクライアント (呼び出し元) の間で暗黙的に指定されたコントラクトを記述でき、高速の不変性とその他のプロパティがさらのプログラムの分析の向上します。

 SAL は、さまざまな種類のロック プリミティブをサポートしています: クリティカル セクション、ミュー テックス、スピン ロック、およびその他のリソース オブジェクト。 多くの同時実行の注釈では、パラメーターとしてのロックの式を使用します。 慣例により、ロックは、基になるロック オブジェクトのパス式で表されます。

 いくつかスレッドの所有権ルールに注意してください。

-   スピン ロックは、クリア スレッド所有権のあるカウントされないロックです。

-   ミュー テックスとクリティカル セクションには、クリア スレッド所有権のロックがカウントされます。

-   セマフォおよびイベントには、クリア スレッドの所有権がないロックがカウントされます。

## <a name="locking-annotations"></a>ロックの注釈
 次の表は、ロックの注釈を一覧表示します。

|注釈|説明|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|関数に注釈を付けますことの投稿で、関数の状態を 1 つ増やしますによって指定されるロック オブジェクトの排他ロックの数を示し`expr`します。|
|`_Acquires_lock_(expr)`|関数に注釈を付けますこと投稿状態関数を 1 つ増やしますによって指定されるロック オブジェクトのロック カウントを示し`expr`します。|
|`_Acquires_nonreentrant_lock_(expr)`|によって指定されるロック`expr`が取得されます。  エラーは、ロックが既に保持されている場合に報告されます。|
|`_Acquires_shared_lock_(expr)`|関数に注釈を付けますこと post で関数の状態を 1 つ増やしますによって指定されるロック オブジェクトの共有ロックの数を示し`expr`します。|
|`_Create_lock_level_(name)`|シンボルを宣言するステートメント`name`ロック レベルを注釈内で使用できるように`_Has_Lock_level_`と`_Lock_level_order_`します。|
|`_Has_lock_kind_(kind)`|任意のオブジェクトをリソース オブジェクトの型情報を絞り込むに注釈を付けます。 異なる種類のリソースに共通の型を使用することがあり、オーバー ロードされた型はさまざまなリソース間でのセマンティックの要件を区別するためには不十分です。 一覧をここでは定義済み`kind`パラメーター。<br /><br /> `_Lock_kind_mutex_`<br /> ミュー テックスのロックの種類 ID。<br /><br /> `_Lock_kind_event_`<br /> イベントの種類の ID をロックします。<br /><br /> `_Lock_kind_semaphore_`<br /> セマフォのロックの種類 ID。<br /><br /> `_Lock_kind_spin_lock_`<br /> スピン ロックのロックの種類 ID。<br /><br /> `_Lock_kind_critical_section_`<br /> クリティカル セクションのロックの種類 ID。|
|`_Has_lock_level_(name)`|ロック オブジェクトに注釈を付けますのロック レベルが与えられます`name`します。|
|`_Lock_level_order_(name1, name2)`|ステートメントの間で順序付けのロックを`name1`と`name2`します。|
|`_Post_same_lock_(expr1, expr2)`|関数に注釈を付けます示し、2 つのロックを状態 post で`expr1`と`expr2`は、同じロック オブジェクトとして扱われます。|
|`_Releases_exclusive_lock_(expr)`|関数に注釈を付けます、投稿を 1 つによって指定されるロック オブジェクトの排他ロックの数の関数をデクリメント状態ことを示します`expr`します。|
|`_Releases_lock_(expr)`|関数に注釈を付けます、投稿を 1 つのロック オブジェクトによって指定されるロックの数の関数をデクリメント状態ことを示します`expr`します。|
|`_Releases_nonreentrant_lock_(expr)`|によって指定されるロック`expr`解放されます。 エラーは、ロックが現在保持していない場合に報告されます。|
|`_Releases_shared_lock_(expr)`|関数に注釈を付けます、投稿を 1 つの共有ロックのロック オブジェクトによって指定される数の関数をデクリメント状態ことを示します`expr`します。|
|`_Requires_lock_held_(expr)`|関数に注釈を付けます示し、によって指定されるオブジェクトのロック カウントを状態より前で`expr`は少なくとも 1 つです。|
|`_Requires_lock_not_held_(expr)`|関数に注釈を付けます示し、によって指定されるオブジェクトのロック カウントを状態より前で`expr`は 0 です。|
|`_Requires_no_locks_held_`|関数に注釈を付けます、前提条件チェッカーで認識されているすべてのロックのロック カウントがゼロであることを示します。|
|`_Requires_shared_lock_held_(expr)`|関数に注釈を付けます示し、によって指定されるオブジェクトの共有ロックの数を状態より前で`expr`は少なくとも 1 つです。|
|`_Requires_exclusive_lock_held_(expr)`|関数に注釈を付けます示し、によって指定されるオブジェクトの排他ロックの数を状態より前で`expr`は少なくとも 1 つです。|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>非公開のロック オブジェクトに対する SAL の組み込み
 関連付けられたロック関数の実装によっては、特定のロック オブジェクトは公開されません。  次の表には、それらの非公開のロック オブジェクトを操作する関数の注釈を有効にする SAL の組み込み変数が一覧表示します。

|注釈|説明|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|キャンセルのスピン ロックをについて説明します。|
|`_Global_critical_region_`|クリティカル領域をについて説明します。|
|`_Global_interlock_`|インタロックされた操作をについて説明します。|
|`_Global_priority_region_`|優先リージョンをについて説明します。|

## <a name="shared-data-access-annotations"></a>共有データ アクセスの注釈
 次の表は、共有データ アクセスの注釈を一覧表示します。

|注釈|説明|
|----------------|-----------------|
|`_Guarded_by_(expr)`|変数に注釈を付けます示し、そのたびに、変数がアクセスされる、によって指定されるロック オブジェクトのロック カウント`expr`は少なくとも 1 つです。|
|`_Interlocked_`|変数に注釈を付けます、等価`_Guarded_by_(_Global_interlock_)`します。|
|`_Interlocked_operand_`|注釈付きの関数パラメーターは、さまざまな Interlocked 関数の 1 つのターゲットのオペランドです。  これらのオペランドは、特定の追加プロパティを持つ必要があります。|
|`_Write_guarded_by_(expr)`|変数に注釈を付けますするたびに、変数を変更、ロックのロック オブジェクトによって指定される数を示します`expr`は少なくとも 1 つです。|

## <a name="see-also"></a>関連項目

- [SAL 注釈を使って C/C++ のコード障害を減らす方法](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL について](../code-quality/understanding-sal.md)
- [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)
- [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)
- [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)
- [注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [組み込み関数](../code-quality/intrinsic-functions.md)
- [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)
- [コード分析チームのブログ](http://go.microsoft.com/fwlink/p/?LinkId=251197)