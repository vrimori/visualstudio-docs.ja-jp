---
title: "組み込み関数 | Microsoft Docs"
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
  - "_String_length_"
  - "_Param_"
  - "_Curr_"
  - "_Old_"
  - "_Nullterm_length_"
  - "_Inexpressible_"
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 組み込み関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

SAL の式は、C\+\+ 効果の側がない式で C\+\+ のは. \/C C\+\+ の式である必要があります。。、関数の呼び出しは、このコンテキストに副作用が生じます。ただし、SAL で SAL 式で使用できる予約済みシンボルや関数に似たオブジェクトを提供します。  これらは、*組み込み関数*と呼ばれます。  
  
## 汎用  
 次の instrinsic 関数は、SAL 注釈に汎用ユーティリティが用意されています。  
  
|注釈|説明|  
|--------|--------|  
|`_Curr_`|現在指定されているオブジェクトのシノニムです。`_At_` の注釈が使用中の場合、`_Curr_` は `_At_`を最初のパラメーターと同じです。それ以外の場合、パラメーターまたは注釈が構文的に関連付けられた関数全体と戻り値です。|  
|`_Inexpressible_(expr)`|入力データをスキャンして、選択したメンバーをカウント算出されたときにバッファーのサイズが例や式の注釈を使用して表すには、複雑な状況を表します。|  
|`_Nullterm_length_(param)`|`param` は null 終端文字バッファーより前の要素の数です。  これは非集約非 void 型の任意のバッファーに適用される可能性があります。|  
|`_Old_(expr)`|これは事前条件で評価される場合、`_Old_` は入力値 `expr`を返します。これは後条件で評価される場合、事前条件で評価されます。`expr` 値を返します。|  
|`_Param_(n)`|関数の `n`th パラメーター、1 から `n`にカウント、および `n` はリテラル整数の定数です。  パラメーターがある場合、この注釈は、パラメーターに名前でアクセスすることと同じです。 **Note:**  `n` は 省略記号で位置指定パラメーターを示す定義されている可能性がある、または名前を使用しない関数プロトタイプで使用されることがあります。|  
|`return`|SAL の式で C\/C\+\+ の予約済みのキーワード `return` が関数の戻り値を参照することができます。値が POST の状態でのみ使用できます。; これは、以前に使用する構文エラー状態になります。|  
  
## 文字列固有  
 次の組み込み関数の注釈は文字列の操作を有効にします。  これらの関数の 4 つが、すべて同じで: null 終端文字の前にある型の要素数を返します。  違いは、参照される要素のデータ型です。  文字で構成される null で終わるなバッファーの長さを指定する場合は、前のセクションの `_Nullterm_length_(param)` の注釈を使用していることに注意してください。  
  
|注釈|説明|  
|--------|--------|  
|`_String_length_(param)`|`param` は null 終端文字より前 Strings 要素の数です。  この注釈は、文字列の文字型のために予約されています。|  
|`strlen(param)`|`param` は null 終端文字より前 Strings 要素の数です。  この注釈は、文字配列で使用するために予約されているため、C ランタイム関数 [strlen \(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)に似ています。|  
|`wcslen(param)`|`param` は \(ただし、\) が null 終端文字まで文字列の要素の数です。  この注釈はワイド文字の配列で使用するために予約されているため、C ランタイム関数 [wcslen \(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)に似ています。|  
  
## 参照  
 [SAL 注釈を使って C\/C\+\+ のコード障害を減らす方法](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)