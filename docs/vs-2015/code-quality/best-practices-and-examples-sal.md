---
title: ベスト プラクティスと例 (SAL) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9327ab850bb5f62158e48abc4c8445d3f9b6fe9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743741"
---
# <a name="best-practices-and-examples-sal"></a>ベスト プラクティスと例 (SAL)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

最もからソース コード注釈言語 (SAL) を取得し、一般的な問題を回避する方法を示します。  
  
## <a name="in"></a>\_In\_
 関数は、要素を記述することになって場合を使用して、`_Inout_`の代わりに`_In_`します。 これは、古いマクロから SAL への自動変換の場合に特に関連します。 SAL、前に多くのプログラマがコメントとしてマクロを使用: 名前を付けられたマクロ`IN`、 `OUT`、 `IN_OUT`、またはこれらの名前のバリアント。 これらのマクロは、SAL を変換することをお勧めも強くお勧めすると、元のプロトタイプが作成されており、古いマクロが、コードが何を反映していないために、コードが変更されている可能性がありますので変換する際は注意してください。 詳細については、特に注意してください、`OPTIONAL`マクロを頻繁に正しく配置されていないため、コメント: コンマの反対側になど。  
  
```cpp  
  
// Incorrect  
void Func1(_In_ int *p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
// Correct  
void Func2(_Inout_ PCHAR p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
```  
  
## <a name="opt"></a>\_opt\_  
 呼び出し元が null ポインターを渡すことを許可されていない場合は、使用`_In_`または`_Out_`の代わりに`_In_opt_`または`_Out_opt_`します。 これをそのパラメーターをチェックし、エラーが返されますが NULL であることがない場合に関数にも当てはまります。 適切な防御的なコーディング方法では、関数は、予期しない NULL のパラメーターをチェックおよび適切に返すことが必ずしも省略可能な型のパラメーターの注釈ができること (\_*Xxx*_opt\_).  
  
```cpp  
  
// Incorrect  
void Func1(_Out_opt_ int *p1)  
{  
    *p = 1;  
}  
  
// Correct  
void Func2(_Out_ int *p1)  
{  
    *p = 1;  
}  
  
```  
  
## <a name="predefensive-and-postdefensive"></a>\_Pre_defensive\_と\_Post_defensive\_  
 使用することをお勧め関数は、信頼境界に表示されている場合、`_Pre_defensive_`注釈。  「防御的な」修飾子が呼び出しの時点で、いることを示す特定のコメントを変更します、インターフェイスを厳密には、チェックする必要がありますが実装ボディ内にする必要があります前提として不正確なパラメーターを渡すことができます。 その場合は、`_In_ _Pre_defensive_`を呼び出し元には、NULL を渡すしようとすると、エラーが発生、が関数本体分析パラメーターが NULL の場合、最初にポインターを逆参照しようする可能性がありますかのように提供することを示すために信頼境界をお勧めNULL の確認にはフラグが付けられます。  A`_Post_defensive_`注釈は、コールバックの場所、信頼されたパーティは、呼び出し元と見なされ、信頼できないコードが呼び出されたコードで使用できることもできます。  
  
## <a name="outwrites"></a>\_Out_writes\_  
 次の例での一般的な誤用`_Out_writes_`します。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 注釈`_Out_writes_`バッファーがあることを示します。 `cb`初期化終了時に最初のバイトで、割り当てられたバイト数。 この注釈が厳密に正しくないと、割り当てサイズを表現することをお勧めします。 ただし、示されていない要素の数が、関数によって初期化されます。  
  
 次の例では、完全にバッファーの初期化の部分の正確なサイズを指定する 3 つの正しい方法を示します。  
  
```cpp  
  
// Correct  
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,   
    DWORD size,  
    PDWORD pCount  
);  
  
void Func2(_Out_writes_all_(size) CHAR *pb,   
    DWORD size  
);  
  
void Func3(_Out_writes_(size) PSTR pb,   
    DWORD size  
);  
  
```  
  
## <a name="out-pstr"></a>\_Out\_ PSTR  
 使用`_Out_ PSTR`がほぼ常に間違っています。 これは、文字バッファーを指す出力パラメーターを持つものとして解釈され、NULL で終わることをお勧めします。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 注釈のような`_In_ PCSTR`は一般的で便利です。 NULL で終わるを持つため、入力文字列の指すの precondition`_In_`により、NULL で終わる文字列を認識します。  
  
## <a name="in-wchar-p"></a>\_\_ WCHAR * p  
 `_In_ WCHAR* p` 入力のポインターがあることを示す`p`1 つの文字を指します。 ただし、ほとんどの場合、これはない可能性がありますが想定されている仕様です。 代わりは NULL で終わる配列の指定は、おそらく対象としていますそのために使用`_In_ PWSTR`します。  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 NULL 終了の適切な仕様が不足しているが一般的です。 使用して、適切な`STR`バージョンを次の例に示すように、型を置き換えます。  
  
```cpp  
  
// Incorrect  
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
// Correct  
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
```  
  
## <a name="outrange"></a>\_Out_range\_  
 パラメーターがポインターであり使用して、ポインターが指している要素の値の範囲を表現したい場合`_Deref_out_range_`の代わりに`_Out_range_`します。 次の例の範囲で * pcbFilled を表現すると、pcbFilled ではありません。  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Out_range_(0, cbSize) DWORD *pcbFilled  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled   
);  
  
```  
  
 `_Deref_out_range_(0, cbSize)` 推測するためにはいくつかのツールには必須ではありません`_Out_writes_to_(cbSize,*pcbFilled)`が完全を期すのためここで表示されます。  
  
## <a name="wrong-context-in-when"></a>コンテキストが正しくない\_とき\_  
 もう 1 つのよくある間違いでは、前提条件の後の状態の評価を使用します。 次の例では、`_Requires_lock_held_`の前提条件です。  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 式`result`前の状態では利用できません後の状態の値を参照します。  
  
## <a name="true-in-success"></a>場合は TRUE\_成功。\_  
 戻り値が 0 以外の場合、関数が成功した場合は、使用`return != 0`の代わりに、成功条件として`return == TRUE`します。 0 以外は必ずしものコンパイラを提供する実際の値の等価性`TRUE`します。 パラメーターを`_Success_`式であるし、対応すると、次の式が評価されます: `return != 0`、 `return != false`、 `return != FALSE`、および`return`パラメーターや比較は不要です。  
  
```cpp  
  
// Incorrect  
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
// Correct  
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
```  
  
## <a name="reference-variable"></a>参照変数  
 参照変数、以前のバージョンの SAL 注釈の対象として、暗黙的なポインターを使用およびの追加に必要な`__deref`to 参照変数に接続されている注釈。 このバージョンは、オブジェクト自体を使用し、追加は必要ありません`_Deref_`します。  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
```  
  
## <a name="annotations-on-return-values"></a>戻り値に関する注釈  
 次の例では、戻り値の注釈内で一般的な問題を示します。  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 この例で`_Out_opt_`という、ポインターが前提条件の一部として NULL をする可能性があります。 ただし、前提条件は、戻り値に適用できません。 適切な注釈は、この場合、`_Ret_maybenull_`します。  
  
## <a name="see-also"></a>関連項目  
 [SAL 注釈を使用して C/C++ のコード障害を減らす](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所を指定します。](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [組み込み関数](../code-quality/intrinsic-functions.md)



