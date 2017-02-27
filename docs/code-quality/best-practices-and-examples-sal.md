---
title: "ベスト プラクティスと例 (SAL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# ベスト プラクティスと例 (SAL)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ほとんどのソース・コード注釈言語 \(SAL\) から取得し、一般的な問題を回避する方法を次に示します。  
  
## \_In\_  
 関数が要素に書き込むように想定されて `_In_`の代わりに `_Inout_` を使用します。  これは、以前のマクロの SAL への自動変換の場合に特に関連しています。  SAL 前に、多くのプログラマは、これらの名前の `IN`、`OUT`、`IN_OUT`、VARIANT というコメント マクロとしてマクロを使用します。  SAL にこれらのマクロを変換することが推奨されますが、これは、元のプロトタイプが書き込まれ、古いマクロは、コードの動作に影響を与える可能性があるため、コードが変更される可能性があるため、これらを変換するときに注意する必要がせき立てます。  例不適切でよくしまうため、コンマの部分に `OPTIONAL` のコメントのマクロについて特に注意してください。  
  
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
  
## \_opt\_  
 呼び出し元が `_In_opt_` または `_Out_opt_`の代わりに使用 `_In_` null ポインター、または `_Out_` を渡すことはできません。  これはパラメーターをチェックし、エラーを返す関数に指定する必要がない場合は、空白に適用されます。  この関数はを持つと予期しない NULL のパラメーター、およびは適切な積極的なコーディング手法ですが、パラメーター注釈が省略可能な型 \(\_Xxx\_opt\_\) できることを意味しません。  
  
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
  
## \_Pre\_defensive\_ および \_Post\_defensive\_  
 関数が信頼の境界線で表示されている場合は、`_Pre_defensive_` の注釈を使用することをお勧めします。「積極的な」修飾子は、呼び出しの時点で、インターフェイスを厳密にチェックされる実装の本体に無効なパラメーターが渡される可能性があることを想定する必要があることを示すために、特定の注釈を変更します。  その場合は、呼び出し元がパラメーターが null である可能性があります。最初の空白があることを確認してからのポインターを逆参照しようとすると、フラグが立てられるように NULL を渡すと、エラーが発生しますが、関数本体は、分析することを示すために、`_In_ _Pre_defensive_` は信頼の境界であり。`_Post_defensive_` の注釈が信頼パーティが呼び出し元の想定される信頼されていないコードが呼び出されたコードであるコールバックで使用するためにも使用できます。  
  
## \_Out\_writes\_  
 次の例では `_Out_writes_`の誤用を示しています。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 バッファーが `_Out_writes_` 注釈を示します。  これは `cb` バイトを終了時に初期化されて、最初のバイトを割り当てています。  この注釈は、厳密には表示されず、割り当てられたサイズを表現できると便利です。  ただし、要素が関数で初期化される場合、決まるわけではありません。  
  
 次の例は、完全に初期化されたバッファーの部分の絶対サイズを指定するには、3 とおりの正しい方法。  
  
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
  
## \_Out\_ PSTR  
 `_Out_ PSTR` の使用には不適切です。  これは解釈され、文字バッファーへのポインターが null で終わるである出力パラメーターを持つとします。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 `_In_ PCSTR` などの注釈は共通と便利です。  これは \(終端の null を含む入力文字列を `_In_` の事前条件が null で終わる文字列を認識できるようにするためです。  
  
## \_In\_ WCHAR\* p  
 `_In_ WCHAR* p` は 入力ポインター `p` が 1 文字に向いていることを通知します。  ただし、ほとんどの場合、これは、意図したものではありません。  代わりに、意図したとおりに、null で終わるな配列の;仕様です。これを行うには、`_In_ PWSTR`を使用します。  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 NULL 終端の適切な仕様が欠落していることが一般的です。  次の例に示すように、型を置き換えるに `STR` 適切なバージョンを使用します。  
  
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
  
## \_Out\_range\_  
 パラメーターがポインターであり、ポインターが指す要素の値の範囲を表現するには、`_Out_range_`の代わりに `_Deref_out_range_` を使用します。  次の例では、\*pcbFilled の範囲が表示されたら、は pcbFilled。  
  
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
  
 `_Deref_out_range_(0, cbSize)` は 一部のツールには、`_Out_writes_to_(cbSize,*pcbFilled)`から推論できますが、完全を期すために、ここに示されているためです。  
  
## \_When\_ の間違ったコンテキスト  
 もう一つのよくある間違いの事前条件の状態に後の評価を使用します。  次の例では、`_Requires_lock_held_` は事前条件です。  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 式 `result` は前の状態で使用できないと状態の値を示します。  
  
## \_Success\_ の TRUE  
 戻り値が 0 以外のであると関数が正常に終了した場合、`return == TRUE`の代わりに成功の状態として `return != 0` を使用します。  0 以外の、コンパイラが `TRUE`に提供する実際の値と同等ではありません。  `_Success_` へのパラメーターは式であり、次の式は等価として評価される: パラメーターまたは比較なしの `return != 0`、`return != false`、`return != FALSE`と `return`。  
  
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
  
## 参照変数  
 参照変数には、SAL の以前のバージョンでは、注釈ターゲットとして暗黙のポインターを使用し、参照変数にアタッチされたコメントに `__deref` を追加する必要がありました。  このバージョンは、オブジェクト自体を使用して、追加 `_Deref_`は必要ではありません。  
  
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
  
## 戻り値に関する注釈  
 次の例は、一般的な問題値の注釈を戻り値として示します。  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 この例では、`_Out_opt_` はポインターが事前条件の一部として null である可能性があることを通知します。  ただし、事前条件は戻り値に適用できません。  この場合、正しい注釈は `_Ret_maybenull_`です。  
  
## 参照  
 [SAL 注釈を使って C\/C\+\+ のコード障害を減らす方法](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [組み込み関数](../code-quality/intrinsic-functions.md)