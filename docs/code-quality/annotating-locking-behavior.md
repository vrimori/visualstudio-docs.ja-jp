---
title: "ロック動作に注釈を付ける |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0fa6ecdef564f7911e6de09ad56b5934e9231f35
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="annotating-locking-behavior"></a>ロック動作に注釈を付ける
常に、マルチ スレッド プログラムでバグを同時実行を避けるためには、以下の適切なロック作業分野と SAL 注釈を使用します。  
  
 同時実行のバグが再現、診断、およびは非決定的であるために、デバッグに非常に困難です。 スレッドがインターリーブについて推論困難最高では、現実的では複数のスレッドがあるコードの本文をデザインする場合。 そのためはマルチ スレッド プログラムで、ロック作業分野に従うことをお勧めします。 たとえば、ロックの順序を名実、デッドロックを回避するには複数のロックを設定して、共有リソースにアクセスする前に適切な guarding ロックを獲得する競合状態の防止に役立ちます。  
  
 残念ながら、一見単純ロック ルール驚くほど難しくなりますのプラクティスに従ってください。 今日のプログラミング言語およびコンパイラの基本的な制限は、こと、直接サポートしない仕様と同時実行要件の分析です。 プログラマは、非公式なコードのコメントについてロックを使用する自分の意図を表すために依存する必要があります。  
  
 同時実行 SAL 注釈は、担当、データ guardianship、ロック順序階層、および必要なその他のロック動作をロック、ロックの副作用を指定するために設計されています。 暗黙的な規則を明示的に行うでは、同時実行の SAL 注釈は、コードがロックの規則を使用する方法を文書化するための一貫した方法を提供します。 同時実行の注釈には、競合状態、デッドロック、不一致の同期操作、およびその他の同時実行の微妙なエラーを検索するコード分析ツールの機能も強化します。  
  
## <a name="general-guidelines"></a>一般的なガイドライン  
 注釈を使用すると、(呼び出し) の実装とクライアント (呼び出し元) の間の関数の定義によって暗黙的に指定されたコントラクトを記述して高速不変式とその他のプロパティをさらに、プログラムの分析の向上します。  
  
 SAL は、さまざまな種類のロック プリミティブをサポートしています: クリティカル セクション、ミュー テックス、スピン ロック、およびその他のリソース オブジェクト。 多くの同時実行注釈では、パラメーターとしてロック式を受け取る。 慣例により、ロックは、基になるロック オブジェクトのパス式で表されます。  
  
 いくつかのスレッド所有者の規則に留意してください:  
  
-   スピン ロックは、クリア スレッドの所有権がカウントされないロックです。  
  
-   ミュー テックスと重要なセクションには、クリア スレッドの所有権のロックがカウントされます。  
  
-   セマフォおよびイベントには、クリア スレッドの所有権を持たないロックがカウントされます。  
  
## <a name="locking-annotations"></a>ロックの注釈  
 次の表は、ロックの注釈を一覧表示します。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|関数の注釈を示し、こと投稿状態関数は、いずれかで排他ロックのカウントをインクリメントはロック オブジェクトによって指定される`expr`です。|  
|`_Acquires_lock_(expr)`|関数の注釈を付けますことを示し、投稿状態関数は、いずれかによってロック カウントをインクリメントによって指定されるロック オブジェクトの`expr`します。|  
|`_Acquires_nonreentrant_lock_(expr)`|によって指定されるロック`expr`を取得します。  ロックが既に保持されている場合、エラーが報告されます。|  
|`_Acquires_shared_lock_(expr)`|関数の注釈を示し、こと投稿状態関数は、いずれかによって、共有ロックのカウントをインクリメントはロック オブジェクトによって指定される`expr`です。|  
|`_Create_lock_level_(name)`|シンボルを宣言するステートメント`name`ロック レベルを注釈に使用できるように`_Has_Lock_level_`と`_Lock_level_order_`です。|  
|`_Has_lock_kind_(kind)`|任意のオブジェクトをリソース オブジェクトの種類の情報を絞り込むための注釈を付けます。 異なる種類のリソースの共通の型を使用することがあり、オーバー ロードされた型はさまざまなリソース間のセマンティックの要件を区別するのに十分ではありません。 ここでは、一連の定義済み`kind`パラメーター。<br /><br /> `_Lock_kind_mutex_`<br /> ミュー テックスの種類の ID をロックします。<br /><br /> `_Lock_kind_event_`<br /> イベントの種類の ID をロックします。<br /><br /> `_Lock_kind_semaphore_`<br /> セマフォの種類の ID をロックします。<br /><br /> `_Lock_kind_spin_lock_`<br /> スピン ロックの種類の ID をロックします。<br /><br /> `_Lock_kind_critical_section_`<br /> クリティカル セクションのロックの種類 ID。|  
|`_Has_lock_level_(name)`|注釈をロック オブジェクトとのロック レベルが与えられます`name`です。|  
|`_Lock_level_order_(name1, name2)`|ステートメントの間で順序付けのロックを`name1`と`name2`です。|  
|`_Post_same_lock_(expr1, expr2)`|関数の注釈を示し、2 つのロックを状態投稿`expr1`と`expr2`は、同じロック オブジェクトとして扱われます。|  
|`_Releases_exclusive_lock_(expr)`|関数の注釈を付けますおよび投稿によって指定されるロック オブジェクトの排他ロック カウントを 1 つの関数をデクリメント状態ことを示す`expr`です。|  
|`_Releases_lock_(expr)`|関数の注釈を付けますおよび投稿によって指定されるロック オブジェクトのロック カウントを 1 つの関数をデクリメント状態ことを示す`expr`です。|  
|`_Releases_nonreentrant_lock_(expr)`|によって指定されるロック`expr`を解放します。 ロックが保持されてい場合は、エラーが報告されます。|  
|`_Releases_shared_lock_(expr)`|関数の注釈を付けますおよび投稿では共有ロックの数はロック オブジェクトによって指定される 1 つの関数をデクリメント状態ことを示す`expr`です。|  
|`_Requires_lock_held_(expr)`|関数の注釈を示し、によって指定されるオブジェクトのロック数を状態前に`expr`が少なくとも 1 つです。|  
|`_Requires_lock_not_held_(expr)`|関数の注釈を示し、によって指定されるオブジェクトのロック数を状態前に`expr`ゼロです。|  
|`_Requires_no_locks_held_`|関数の注釈し、チェッカーに認識されているすべてのロックのロック カウントがゼロであることを示します。|  
|`_Requires_shared_lock_held_(expr)`|関数の注釈を示し、によって指定されるオブジェクトの共有ロックの数を状態前に`expr`が少なくとも 1 つです。|  
|`_Requires_exclusive_lock_held_(expr)`|関数の注釈を示し、によって指定されるオブジェクトの排他ロックの数を状態前に`expr`が少なくとも 1 つです。|  
  
## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>非公開のロック オブジェクトに対する SAL の組み込み  
 関連付けられたロック関数の実装によっては、ロックの特定のオブジェクトは公開されません。  次の表には、それらの非公開のロック オブジェクトを操作する関数の注釈を有効にする SAL の組み込み変数が一覧表示します。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_Global_cancel_spin_lock_`|[キャンセル] スピン ロックをについて説明します。|  
|`_Global_critical_region_`|重要な領域をについて説明します。|  
|`_Global_interlock_`|インタロックされた操作をについて説明します。|  
|`_Global_priority_region_`|優先順位の領域について説明します。|  
  
## <a name="shared-data-access-annotations"></a>共有データ アクセスの注釈  
 次の表は、共有データ アクセスの注釈を一覧表示します。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_Guarded_by_(expr)`|注釈を変数を示し、ときに、変数にアクセスすること、によって指定されるロック オブジェクトのロック カウント`expr`が少なくとも 1 つです。|  
|`_Interlocked_`|変数の注釈し、同等です`_Guarded_by_(_Global_interlock_)`です。|  
|`_Interlocked_operand_`|注釈付きの関数パラメーターは、さまざまな Interlocked 関数のいずれかのターゲットのオペランドです。  これらのオペランドは、特定の追加のプロパティが必要です。|  
|`_Write_guarded_by_(expr)`|変数の注釈し、するたびに、変数を変更、によって指定されるロック オブジェクトのロック カウントを示す`expr`が少なくとも 1 つです。|  
  
## <a name="see-also"></a>関連項目  
 [C/C++ コード障害を減らす SAL 注釈の使用](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈を付ける](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [注釈を適用するタイミングと場所を指定します。](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [組み込み関数](../code-quality/intrinsic-functions.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)   
 [コード分析チームのブログ](http://go.microsoft.com/fwlink/p/?LinkId=251197)