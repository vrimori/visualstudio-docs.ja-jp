---
title: 関数の動作に注釈を付ける |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c061c12e7c34a67692af41b72ea7b04b6f06e07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="annotating-function-behavior"></a>関数の動作に注釈を付ける
注釈を付けるだけでなく[関数パラメーターと戻り値の](../code-quality/annotating-function-parameters-and-return-values.md)、関数全体のプロパティに注釈を付けることができます。  
  
## <a name="function-annotations"></a>関数の注釈  
 次の注釈は、関数全体に適用され、動作や、true にする期待について説明。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|スタンド アロン; を意図していません代わりに、述語で使用するのには、`_When_`注釈。 詳細については、次を参照してください。[を指定すると、注釈の適用先](../code-quality/specifying-when-and-where-an-annotation-applies.md)です。<br /><br /> `name`パラメーターが任意の文字列も含まれている、`_Function_class_`一部の関数の宣言での注釈。  `_Called_from_function_class_` 使用して分析対象関数の注釈が付けられている場合は 0 以外を返します`_Function_class_`の同じ値を持つ`name`以外の場合、0 を返します。|  
|`_Check_return_`|戻り値の注釈を付けますされ、それを呼び出し元で調べる必要があります。 チェッカーは、void のコンテキストで関数が呼び出された場合に、エラーを報告します。|  
|`_Function_class_(name)`|`name`パラメーターは、ユーザーが指定されている任意の文字列。  他の名前空間と異なる名前空間内に存在します。 関数、関数ポインター、または — 意義のある最も: 関数ポインターの型は、1 つまたは複数の関数クラスに属するものとして指定することができます。|  
|`_Raises_SEH_exception_`|常に対象に、構造化例外ハンドラー (SEH) 例外を発生させている関数の注釈を付けます`_When_`と`_On_failure_`条件。 詳細については、次を参照してください。[を指定すると、注釈の適用先](../code-quality/specifying-when-and-where-an-annotation-applies.md)です。|  
|`_Maybe_raises_SEH_exception_`|対象に、SEH 例外を発生する可能性が必要に応じて、関数の注釈を付けます`_When_`と`_On_failure_`条件。|  
|`_Must_inspect_result_`|戻り値、パラメーター、およびグローバル変数を含む、出力値の注釈を付けます。  アナライザーは、注釈付きオブジェクトの値が、後で検査しない場合、エラーを報告します。 「検査」には、条件式で使用される、出力パラメーターに割り当てられているか、グローバル、または、パラメーターとして渡されるかどうかが含まれています。  戻り値は、`_Must_inspect_result_`意味`_Check_return_`です。|  
|`_Use_decl_annotations_`|ヘッダー内の注釈の一覧の代わりに、関数の定義 (関数本体とも呼ばれます) に使用することはできます。  ときに`_Use_decl_annotations_`はこれを使用すると、同じ関数、スコープ内のヘッダーに表示される注釈使用として存在する場合もある定義内、`_Use_decl_annotations_`注釈。|  
  
## <a name="successfailure-annotations"></a>成功または失敗の注釈  
 関数が失敗し、時に、その結果が不完全でも関数が成功したときに、結果と異なります。  次の一覧に注釈は、エラー時の動作を表す方法を提供します。  これらの注釈を使用するには、必要がありますを有効にした成功を判断します。したがって、`_Success_`注釈が必要です。  注意して`NTSTATUS`と`HRESULT`が既にある、`_Success_`に組み込まれている注釈ただしを指定する場合、独自`_Success_`注釈で`NTSTATUS`または`HRESULT`、組み込みの注釈よりも優先されます。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_Always_(anno_list)`|等価`anno_list _On_failure_(anno_list)`; 内の注釈は、`anno_list`関数が成功したかどうかを適用します。|  
|`_On_failure_(anno_list)`|使用する場合にのみ`_Success_`は関数の注釈を設定にも使用 — 明示的または暗黙的にを通じて`_Return_type_success_`typedef にします。 ときに、`_On_failure_`注釈は、関数パラメーターまたは戻り値の各注釈上に存在`anno_list`(anno) として記述されている場合と同様に動作`_When_(!expr, anno)`ここで、 `expr` 、必須のパラメーターは、`_Success_`注釈。 つまり、この暗黙のアプリケーションの`_Success_`後のすべての条件には適用されません`_On_failure_`です。|  
|`_Return_type_success_(expr)`|Typedef に適用できます。 すべての機能を入力し、明示的がないことを返すことを示す`_Success_`注釈が付けられていましたまるで`_Success_(expr)`です。 `_Return_type_success_` 関数または関数ポインターの typedef では使用できません。|  
|`_Success_(expr)`|`expr` 右辺値を生成する式です。 ときに、`_Success_`関数宣言または定義、それぞれの注釈に注釈がある (`anno`) として記述されている場合と同様の関数と事後条件で動作`_When_(expr, anno)`です。 `_Success_`注釈は関数の場合はそのパラメーターではなくでのみ使用できます、または型を返します。 最大で 1 つできます`_Success_`と関数の場合、上の注釈がいずれかにすることはできません`_When_`、 `_At_`、または`_Group_`です。 詳細については、次を参照してください。[を指定すると、注釈の適用先](../code-quality/specifying-when-and-where-an-annotation-applies.md)です。|  
  
## <a name="see-also"></a>関連項目  
 [C/C++ コード障害を減らす SAL 注釈の使用](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈を付ける](../code-quality/annotating-function-parameters-and-return-values.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所を指定します。](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [組み込み関数](../code-quality/intrinsic-functions.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)