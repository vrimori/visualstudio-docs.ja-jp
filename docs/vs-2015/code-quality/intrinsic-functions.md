---
title: 組み込み関数の |Microsoft Docs
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
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1b50742c0176b8c880d3ed0b58b7b8ef76355777
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174487"
---
# <a name="intrinsic-functions"></a>組み込み関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SAL の式は副作用がない式については、C と C++ の式を指定できます: たとえば、+ +、- と関数の呼び出しがこのコンテキストで副作用があるすべて。  ただし、SAL では、いくつかの関数に似たオブジェクトと SAL 式で使用できるいくつかの予約済みの記号を提供しています。 呼ばれる、*組み込み関数*します。  
  
## <a name="general-purpose"></a>汎用  
 次のいる関数の注釈では、SAL の一般的なユーティリティを提供します。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_Curr_`|注釈が付けられた現在のオブジェクトのシノニムです。  ときに、`_At_`注釈は使用、`_Curr_`は最初のパラメーターと同じ`_At_`します。  それ以外の場合、パラメーターまたは注釈が構文的に関連付けられている全体関数の戻り値になります。|  
|`_Inexpressible_(expr)`|バッファーのサイズが注釈式を使用して表すには複雑すぎる状況を表す — など、入力データセットをスキャンしてカウントし、計算されるメンバーを選択します。|  
|`_Nullterm_length_(param)`|`param` 最大バッファーが null 終端文字を含まない内の要素の数です。 非集計、void 以外の型のすべてのバッファーに適用できます。|  
|`_Old_(expr)`|での前提条件が評価されるときに`_Old_`入力値を返します`expr`します。  事後条件で評価されるときに値を返す`expr`と前提条件で評価された場合します。|  
|`_Param_(n)`|`n`番目のパラメーターを 1 からカウント関数`n`、および`n`リテラル整数の定数します。 場合は、パラメーターの名前は、この注釈は名前で、パラメーターへのアクセスと同じです。 **注:** `n`可能性があります、省略記号によって定義されますか、名前が使用されていない関数プロトタイプで使用できる位置指定パラメーターを参照してください。|  
|`return`|C と C++ の予約済みキーワード`return`関数の戻り値を示す SAL 式で使用できます。  値は、後の状態でのみ使用前の状態で使用すると、構文エラーになります。|  
  
## <a name="string-specific"></a>文字列固有  
 次の組み込み関数の注釈には、文字列の操作が有効にします。 これらの関数の 4 つすべては同じ目的: null 終端文字の前にある型の要素の数を返します。 相違点とは、参照される要素のデータの種類です。 Null で終わるの長さを指定する場合はバッファーされるので注意が文字で構成されませんを使用して、`_Nullterm_length_(param)`前のセクションの注釈。  
  
|注釈|説明|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` 最大文字列が null 終端文字を含まない内の要素の数です。 この注釈は、文字列から文字の種類の予約されています。|  
|`strlen(param)`|`param` 最大文字列が null 終端文字を含まない内の要素の数です。 この注釈は、文字を使用する配列し、C ランタイム関数のように予約されていますが[strlen()](http://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)します。|  
|`wcslen(param)`|`param` 文字列を (が含まれません) 内の要素の数は、null 終端文字。 この注釈は、ワイド文字を使用して配列および C ランタイム関数のように予約されて[wcslen()](http://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)します。|  
  
## <a name="see-also"></a>関連項目  
 [SAL 注釈を使用して C/C++ のコード障害を減らす](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所を指定します。](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)



