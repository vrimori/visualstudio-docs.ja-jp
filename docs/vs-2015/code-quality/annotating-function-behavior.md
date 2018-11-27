---
title: 関数の動作に注釈を付ける |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88213e1cd8112aecac527f7d72d2d74dbf10c559
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783130"
---
# <a name="annotating-function-behavior"></a>関数の動作に注釈を付ける
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注釈を付けるだけでなく[関数パラメーターと戻り値](../code-quality/annotating-function-parameters-and-return-values.md)、関数全体のプロパティに注釈を付けることができます。  
  
## <a name="function-annotations"></a>関数の注釈  
 次の注釈は、全体としての関数に適用し、動作または true 想定されているものを説明します。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|スタンド アロンで; ものでありません。代わりに、述語で使用するが、`_When_`注釈。 詳細については、次を参照してください。[を指定するときと場所の注釈が適用される](../code-quality/specifying-when-and-where-an-annotation-applies.md)します。<br /><br /> `name`パラメーターが任意の文字列にも表示される、`_Function_class_`一部の関数の宣言での注釈。  `_Called_from_function_class_` 使用して分析する関数の注釈を付ける場合は 0 以外を返します`_Function_class_`の同じ値を持つ`name`、それ以外のゼロが返されます。|  
|`_Check_return_`|戻り値の注釈を付けますされ、それを呼び出し元で検査する必要があります。 前提条件チェッカーは、void のコンテキストで関数が呼び出された場合に、エラーを報告します。|  
|`_Function_class_(name)`|`name`パラメーターは、ユーザーが指定されている任意の文字列。  他の名前空間とは別の名前空間に存在します。 関数、関数ポインター、または — 最も有効: 関数ポインターの型は、1 つまたは複数の関数クラスに属するものとして指定することができます。|  
|`_Raises_SEH_exception_`|対象に常に、構造化例外ハンドラー (SEH) 例外を発生させる関数に注釈を付けます`_When_`と`_On_failure_`条件。 詳細については、次を参照してください。[を指定するときと場所の注釈が適用される](../code-quality/specifying-when-and-where-an-annotation-applies.md)します。|  
|`_Maybe_raises_SEH_exception_`|必要に応じて、SEH 例外を対象に生じる可能性がある関数に注釈を付けます`_When_`と`_On_failure_`条件。|  
|`_Must_inspect_result_`|戻り値、パラメーター、およびグローバル変数を含め、すべての出力値の注釈を付けます。  アナライザーは、注釈付きオブジェクトの値が後で検査しない場合、エラーを報告します。 「検査」には、条件付きの式で使用されて、出力パラメーターに割り当てられているか、グローバル、または、パラメーターとして渡されるかどうかが含まれています。  戻り値は、`_Must_inspect_result_`意味`_Check_return_`します。|  
|`_Use_decl_annotations_`|関数の定義 (関数本体とも呼ばれます) で、ヘッダー内の注釈の一覧の代わりに使用できます。  ときに`_Use_decl_annotations_`は、同じ関数、スコープ内のヘッダーに表示される注釈は使用がも定義されている含まれている場合と、`_Use_decl_annotations_`注釈。|  
  
## <a name="successfailure-annotations"></a>成功または失敗の注釈  
 関数が失敗すると、され、その結果が不完全で可能性があるかどうか、または、関数が成功したときに、結果と異なります。  次の一覧に注釈は、エラー動作を表現する方法を提供します。  これらの注釈を使用するには、成功した場合を判断することを有効する必要があります。そのため、`_Success_`注釈が必要です。  注意して`NTSTATUS`と`HRESULT`が既にある、`_Success_`注釈に組み込まれているただし、独自を指定する場合は`_Success_`注釈`NTSTATUS`または`HRESULT`、組み込みの注釈をオーバーライドします。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_Always_(anno_list)`|等価`anno_list _On_failure_(anno_list)`; 内の注釈は、`anno_list`関数が成功したかどうかを適用します。|  
|`_On_failure_(anno_list)`|使用する場合にのみ`_Success_`は関数の注釈を付けるにも使用: 明示的または暗黙的にを通じて`_Return_type_success_`typedef にします。 ときに、`_On_failure_`注釈は、関数パラメーターまたは戻り値、それぞれの注釈で上に存在する`anno_list`(anno) として、コード化された場合と同様に`_When_(!expr, anno)`ここで、`expr`に必要なパラメーターは、`_Success_`注釈。 つまり、暗黙のアプリケーションの`_Success_`後のすべての条件には適用されません`_On_failure_`します。|  
|`_Return_type_success_(expr)`|Typedef には適用可能性があります。 すべての機能を返す型を明示的がないことを示します`_Success_`保持していた場合、注釈が付けられた`_Success_(expr)`します。 `_Return_type_success_` 関数または関数ポインターの typedef では使用できません。|  
|`_Success_(expr)`|`expr` 右辺値を生成する式です。 ときに、`_Success_`注釈は関数宣言または定義、それぞれの注釈の上に存在する (`anno`) 事後条件と、関数での動作として、コード化された場合と`_When_(expr, anno)`します。 `_Success_`注釈はそのパラメーターではなく、関数でのみ使用できます、または型を返します。 最大で 1 つできます`_Success_`関数に注釈がいずれかにすることはできません`_When_`、 `_At_`、または`_Group_`します。 詳細については、次を参照してください。[を指定するときと場所の注釈が適用される](../code-quality/specifying-when-and-where-an-annotation-applies.md)します。|  
  
## <a name="see-also"></a>関連項目  
 [SAL 注釈を使用して C/C++ のコード障害を減らす](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所を指定します。](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [組み込み関数](../code-quality/intrinsic-functions.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)



