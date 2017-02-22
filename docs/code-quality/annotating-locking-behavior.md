---
title: "ロック動作に注釈を付ける | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Releases_nonreentrant_lock_"
  - "_Lock_kind_mutex_"
  - "_Lock_kind_critical_section_"
  - "_Acquires_lock_"
  - "_Releases_lock_"
  - "_Has_lock_kind_"
  - "_Releases_exclusive_lock_"
  - "_Post_same_lock_"
  - "_Requires_exclusive_lock_held_"
  - "_Requires_shared_lock_held_"
  - "_Lock_kind_semaphore_"
  - "_Requires_lock_held_"
  - "_Acquires_exclusive_lock_"
  - "_Create_lock_level_"
  - "_Acquires_nonreentrant_lock_"
  - "_Releases_shared_lock_"
  - "_Has_lock_level_"
  - "_Lock_kind_spin_lock_"
  - "_Requires_lock_not_held_"
  - "_Acquires_shared_lock_"
  - "_Requires_no_locks_held_"
  - "_Lock_level_order_"
  - "_Lock_kind_event_"
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ロック動作に注釈を付ける
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マルチスレッド プログラムの同時実行のバグを回避するには、適切なロックの作業分野に常に従い、SAL 注釈を使用します。  
  
 同時実行のバグは非確定的であるため、再生や診断やデバッグが修復が困難です。  スレッドについて、インタリーブの推論はいくつかのスレッドがより多くのコード本体をデザインしているときに、状態困難だけでなくなります。  したがって、マルチスレッド プログラムのロックの作業分野に従うことをお勧めします。  たとえば、ヘルプがデッドロックを避ける、適切な対策をロック アクセスの共有リソースの前になる競合状態を回避する複数のロックを取得するときに、ロック命令を実行します。  
  
 ただし、見かけ上は単純なロックの規則が実際に従って意外にも困難です。  今日のプログラミング言語およびコンパイラの基本的な制限は、直接同時実行の必要条件の指定と分析をサポートしていません。  プログラマは、簡略的なコード コメントで表現するロックをどのように使用されるかの意図を依存必要があります。  
  
 同時実行の SAL 注釈を担当、データ保護、ロック順序階層およびそのほかの必要なロック動作をロックする副作用のロックを指定できるように設計されています。  暗黙的な規則を明示的に宣言すると、コードが規則をロックすることをどのように使用するかを説明する、SAL 同時実行の注釈では、一貫した方法を提供します。  同時実行のコメントは、コード分析ツールの機能を競合状態、デッドロック、不一致同期操作などの複雑な同時実行エラーのキャッチされます。  
  
## 一般的なガイドライン  
 注釈を使用すると、実装側 \(呼び出し先\) とクライアント側 \(呼び出し元\) 間の関数定義によってコントラクトを示す意味することができ、さらに分析を向上できるプログラムの不変条件などのプロパティを表します。  
  
 SAL は、クリティカル セクション、ミューテックス、スピン ロックなどのプリミティブ リソース オブジェクトのロックのさまざまな種類をサポートします。  同時実行の注釈は、パラメーターとしてロックの式を設定します。  規則では、ロックは、基になるオブジェクトのロック パス式によって表示されます。  
  
 一部は考慮する所有権の規則に対して:  
  
-   スピン ロックが明確なスレッドの所有権を持つ無数のロックです。  
  
-   ミューテックスとクリティカル セクションが明確なスレッドの所有権を持つカウント ロックです。  
  
-   セマフォおよびイベントが明確なスレッドの所有権を持たないカウント ロックです。  
  
## ロックの注釈  
 次の表は、ロックの注釈を示します。  
  
|注釈|説明|  
|--------|--------|  
|`_Acquires_exclusive_lock_(expr)`|関数を使用し、Post 状態で関数が 1 ずつ `expr`で指定されたロック オブジェクトの排他ロックの数をインクリメントすることを示します。|  
|`_Acquires_lock_(expr)`|関数を使用し、Post 状態で関数が 1 ずつ `expr`で指定されたロック オブジェクトのロック カウントをインクリメントすることを示します。|  
|`_Acquires_nonreentrant_lock_(expr)`|`expr` で指定されたロックが取得されます。エラーは、ロックが既に保持されて表示されます。|  
|`_Acquires_shared_lock_(expr)`|関数を使用し、Post 状態で関数が 1 ずつ `expr`で指定されたロック オブジェクトの共有ロックの数をインクリメントすることを示します。|  
|`_Create_lock_level_(name)`|注釈 `_Has_Lock_level_` と `_Lock_level_order_`で使用される、ロックのレベルにあるとシンボル `name` を宣言するステートメント。|  
|`_Has_lock_kind_(kind)`|オブジェクトをリソース オブジェクトの型情報を得るために指定します。  、共通型はリソースの種類に使用され、オーバーロードされた型はさまざまなリソースに意味要件を区別するのに十分ではありません。  `kind` 定義済みパラメーターの一覧を次に示します。:<br /><br /> `_Lock_kind_mutex_`<br /> ミューテックスの種類の ID をロックします。<br /><br /> `_Lock_kind_event_`<br /> イベントの種類の ID をロックします。<br /><br /> `_Lock_kind_semaphore_`<br /> セマフォの種類の ID をロックします。<br /><br /> `_Lock_kind_spin_lock_`<br /> スピン ロックの種類の ID をロックします。<br /><br /> `_Lock_kind_critical_section_`<br /> クリティカル セクションの種類の ID をロックします。|  
|`_Has_lock_level_(name)`|ロック オブジェクトを使用して `name`のロックのレベルを指定します。|  
|`_Lock_level_order_(name1, name2)`|`name1` と `name2`間の順序付けをロックするステートメント。|  
|`_Post_same_lock_(expr1, expr2)`|関数を使用し、同じロック オブジェクトとしてポストの状態に 2 個のロック、`expr1` と `expr2`が、処理されることを示します。|  
|`_Releases_exclusive_lock_(expr)`|関数を使用し、Post 状態で関数が 1 ずつ `expr`で指定されたロック オブジェクトの排他ロックのカウントをデクリメントすることを示します。|  
|`_Releases_lock_(expr)`|関数を使用し、Post 状態で関数が 1 ずつ `expr`で指定されたロック オブジェクトのロック カウントをデクリメントすることを示します。|  
|`_Releases_nonreentrant_lock_(expr)`|`expr` で指定されたロックが解放されます。  エラーは、ロックが現在である報告されます。|  
|`_Releases_shared_lock_(expr)`|関数を使用し、Post 状態で関数が 1 ずつ `expr`で指定されたロック オブジェクトの共有のロック カウントをデクリメントすることを示します。|  
|`_Requires_lock_held_(expr)`|関数を使用し、この状態の `expr` によって指定されるオブジェクトのロック カウントが 1 以上であることを示します。|  
|`_Requires_lock_not_held_(expr)`|関数を使用し、この状態の `expr` によって指定されるオブジェクトのロック カウントがゼロであることを示します。|  
|`_Requires_no_locks_held_`|関数、注釈を付けてチェッカーで認識されるすべてのロックのロック カウントがゼロであることを示します。|  
|`_Requires_shared_lock_held_(expr)`|関数を使用し、この状態の `expr` によって指定されるオブジェクトの共有ロックの数が 1 以上であることを示します。|  
|`_Requires_exclusive_lock_held_(expr)`|関数を使用し、この状態の `expr` によって指定されるオブジェクトの排他ロックの数が 1 以上であることを示します。|  
  
## 非公開のロック オブジェクトに対する SAL の組み込み  
 特定のロック オブジェクトには、関連するロック機能の実装によって公開されません。次の表は、非公開のロック オブジェクトを操作する関数の注釈を使用して SAL の主な変数を示します。  
  
|注釈|説明|  
|--------|--------|  
|`_Global_cancel_spin_lock_`|キャンセルのスピン ロックについて説明します。|  
|`_Global_critical_region_`|クリティカル領域について説明します。|  
|`_Global_interlock_`|インタロックされた操作について説明します。|  
|`_Global_priority_region_`|優先度領域について説明します。|  
  
## 共有データ アクセスの注釈  
 次の表に、共有データ アクセスの注釈を示します。  
  
|注釈|説明|  
|--------|--------|  
|`_Guarded_by_(expr)`|変数にアクセスするたびに変数を使用し、`expr` で指定されたロック オブジェクトのロック カウントは 1 以上であることを示します。|  
|`_Interlocked_`|変数を使用して、`_Guarded_by_(_Global_interlock_)`と同じです。|  
|`_Interlocked_operand_`|注釈付き関数パラメーターはさまざまなインタロックされた関数の 1 種類のターゲット オペランドです。これらのオペランドは固有の追加のプロパティが必要です。|  
|`_Write_guarded_by_(expr)`|変数が変更されるたびに変数を使用し、`expr` で指定されたロック オブジェクトのロック カウントは 1 以上であることを示します。|  
  
## 参照  
 [SAL 注釈を使って C\/C\+\+ のコード障害を減らす方法](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [組み込み関数](../code-quality/intrinsic-functions.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)   
 [分析のチーム ブログをコード。](http://go.microsoft.com/fwlink/p/?LinkId=251197)