---
title: 組み込み関数の |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 932d034fb1510a1e73d439d62ad3129c78841bed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="intrinsic-functions"></a>組み込み関数
SAL の式は副作用がない式であれば、C と C++ の式を指定できます: たとえば、+ +、-- と関数の呼び出しがこのコンテキストですべての副作用であります。  ただし、SAL は一部の関数に似たオブジェクトと SAL 式で使用できるいくつかの予約済みの記号を提供します。 呼ばれる、*の組み込み関数*です。  
  
## <a name="general-purpose"></a>汎用  
 次のいる関数の注釈では、SAL について一般的なユーティリティを提供します。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_Curr_`|注釈が付けられた現在のオブジェクトのシノニムです。  ときに、`_At_`注釈は、使用中`_Curr_`は最初のパラメーターと同じ`_At_`です。  それ以外の場合、パラメーターまたは注釈が構文的に関連付けられている全体関数の戻り値です。|  
|`_Inexpressible_(expr)`|バッファーのサイズが複雑すぎます注釈式を使用している状況を表す — たとえば、によって、入力のデータ セットをスキャンし、カウントし、計算されたメンバーを選択します。|  
|`_Nullterm_length_(param)`|`param` 最大バッファーが null 終端文字を含まない内の要素の数です。 非集計、void でない型のすべてのバッファーにも適用することがあります。|  
|`_Old_(expr)`|前提条件で評価されるときに`_Old_`入力値を返します`expr`です。  事後条件で評価されるときに、値が返されます`expr`ように前提条件の評価されたとします。|  
|`_Param_(n)`|`n`番目のパラメーターを 1 から数えて、関数に`n`、および`n`整数定数のリテラルです。 場合は、パラメーターの名前は、この注釈は名前で、パラメーターへのアクセスと同じです。 **注:** `n`可能性があります、省略記号によって定義されたまたは、名前が使用されていない関数プロトタイプで使用できる位置指定パラメーターを参照してください。  |  
|`return`|C と C++ の予約キーワード`return`関数の戻り値を示すために SAL 式で使用できます。  値は、後の状態でのみ使用これより前の状態で使用する構文エラーです。|  
  
## <a name="string-specific"></a>文字列固有  
 次の組み込み関数の注釈には、文字列の操作が有効にします。 これらの関数の 4 つすべて同じ目的で使用します。 null 終端文字の前にある型の要素の数を取得します。 相違点とは、参照される要素のデータの種類です。 Null で終わるの長さを指定する場合は、バッファーに格納することに注意してくださいは文字で構成されませんを使用して、`_Nullterm_length_(param)`前のセクションの注釈。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` 最大文字列が null 終端文字を含まない内の要素の数です。 この注釈は、文字列から文字の種類用に予約されています。|  
|`strlen(param)`|`param` 最大文字列が null 終端文字を含まない内の要素の数です。 この注釈は予約文字を使用して配列や、C ランタイム関数に似ています[strlen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)です。|  
|`wcslen(param)`|`param` 最大 (含みません)、文字列内の要素の数は、null 終端文字です。 この注釈には、ワイド文字を使用する配列し、C ランタイム関数に似ていますが予約されていますが[wcslen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)です。|  
  
## <a name="see-also"></a>関連項目  
 [C/C++ コード障害を減らす SAL 注釈の使用](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈を付ける](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所を指定します。](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)