---
title: "関数の動作に注釈を付ける | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_On_failure_"
  - "_Return_type_success_"
  - "_Always_"
  - "_Maybe_raises_SEH_exception_"
  - "_Raises_SEH_exception_"
  - "_Called_from_function_class_"
  - "_Function_class_"
  - "_Must_inspect_result_"
  - "_Success_"
  - "_Check_return_"
  - "_Use_decl_annotations_"
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 関数の動作に注釈を付ける
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[関数のパラメーターおよび戻り値](../code-quality/annotating-function-parameters-and-return-values.md)の注釈に加えて、全体のプロパティを使用できます。  
  
## 関数の注釈  
 次の注釈では、全体として関数に適用され、どのように動作するかに原因が true であると想定する方法について説明します。  
  
|注釈|説明|  
|--------|--------|  
|`_Called_from_function_class_(name)`|スタンドアロンの;のものではありません。代わりに、`_When_` 注釈と一緒に使用される述語。  詳細については、「[注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)」を参照してください。<br /><br /> `name` パラメーターは、関数宣言の `_Function_class_` の注釈に表示される任意の文字列です。  `_Called_from_function_class_` は現在分析対象の関数が `_Function_class_` の `name`で同じ値を持つ使用して注釈が 0 以外の返します; それ以外の場合は、ゼロを返します。|  
|`_Check_return_`|戻り値を指定し、それを呼び出し元が確認する必要があることを示します。  チェッカーは関数が void なコンテキストで呼び出された場合、エラーが報告されます。|  
|`_Function_class_(name)`|`name` パラメーターは、ユーザーが指定した任意の文字列です。そのほかの名前空間から別の名前空間にあります。  関数、関数ポインター、または最も usefully\-a 関数ポインターの型は、一つ以上の関数クラスに所属として指定されることがあります。|  
|`_Raises_SEH_exception_`|構造化例外ハンドラー \(SEH\) の例外を常に発生させる `_When_` と `_On_failure_` の状態に応じて関数を使用します。  詳細については、「[注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)」を参照してください。|  
|`_Maybe_raises_SEH_exception_`|オプションで、例外を処理する可能性がある `_When_` と `_On_failure_` の状態に応じて関数を使用します。|  
|`_Must_inspect_result_`|戻り値またはパラメーターとグローバルを含む出力値を指定します。アナライザーは注釈先オブジェクトの値を後で確認するエラーを報告します。「条件式で使用される、出力パラメーターまたはグローバル割り当てられた含まれています。また、パラメーターとして渡されるかどうかを調べるには」。戻り値については、`_Must_inspect_result_` は `_Check_return_`を意味します。|  
|`_Use_decl_annotations_`|ヘッダーで注釈のリストの代わりに関数定義 \(または関数本体\) で使用される場合があります。  `_Use_decl_annotations_` を使用すると、同じ関数のスコープ内のヘッダーに表示される注釈は `_Use_decl_annotations_` の注釈を持つ定義にはいくつかのように使用されます。|  
  
## 成功または失敗の注釈  
 関数が失敗することがありますと関数が成功すると、結果が不完全である場合や、結果が異なる場合があります。次の注釈では、失敗の動作を表現する方法を提供します。これらの注釈を使用するには、それらが成功を判断する必要があります。; したがって、`_Success_` の注釈が必要です。`NTSTATUS` と `HRESULT` には既にに組み込まれている `_Success_` の注釈を付けることに注目してください; ただし、`NTSTATUS` または `HRESULT`で `_Success_` 独自の注釈を指定する場合は、組み込みの注釈をオーバーライドします。  
  
|注釈|説明|  
|--------|--------|  
|`_Always_(anno_list)`|`anno_list _On_failure_(anno_list)`への等価; つまり、`anno_list` の注釈は、関数が成功したかどうかを適用します。|  
|`_On_failure_(anno_list)`|関数のいずれかを明示的に指定するために `_Success_` が使用されている場合にのみ使用されます。または typedef の暗黙的な状態に `_Return_type_success_`。  `_On_failure_` の注釈が関数パラメーターまたは戻り値にときに、anno\) の各注釈は `anno_list``expr` が `_Success_` の注釈にパラメーターであり、`_When_(!expr, anno)`としてコード化されたように動作します。  これはすべての後条件に `_Success_` の暗黙的なアプリケーションが `_On_failure_`に適用されないことを意味します。|  
|`_Return_type_success_(expr)`|typedef に適用される場合があります。  `_Success_(expr)`であったかのようにその型を返し、明示的に `_Success_` を持っていないすべての関数が指定されていることを示します。  `_Return_type_success_` は 関数または関数ポインターの typedef では使用できません。|  
|`_Success_(expr)`|`expr` は 右辺値を表す式です。  `_Success_` の注釈は関数宣言または関数定義と、`_When_(expr, anno)`としてコード化された、関数および後条件の各注釈 \(`anno`\) が実行されます。  `_Success_` の注釈は、パラメーターまたは戻り値の型の関数でのみ、使用される可能性があります。  関数に最大で `_Success_` の 1 種類のコメントがあり、`_When_`、`_At_`、または `_Group_`に置くことはできません。  詳細については、「[注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)」を参照してください。|  
  
## 参照  
 [SAL 注釈を使って C\/C\+\+ のコード障害を減らす方法](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [組み込み関数](../code-quality/intrinsic-functions.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)