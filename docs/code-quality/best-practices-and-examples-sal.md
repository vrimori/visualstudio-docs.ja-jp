---
title: ベスト プラクティスと例 (SAL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8910c9b5d36cecec82bf0e386e294759113c76e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="best-practices-and-examples-sal"></a>ベスト プラクティスと例 (SAL)
最も不足、ソース コード注釈言語 (SAL) を取得し、一般的な問題を回避する方法を示します。

## <a name="in"></a>\_In\_

場合は、関数は、要素への書き込みを想定してを使用して`_Inout_`の代わりに`_In_`です。 これは、古いマクロから SAL への自動変換の場合に特に関連します。 SAL、前に、多くのプログラマはコメントとしてマクロを使用する — という名前がマクロ`IN`、 `OUT`、 `IN_OUT`、またはこれらの名前のバリアント。 SAL をこれらのマクロを変換することをお勧めも」を参照して、コードに変更されたため、元のプロトタイプが作成されており、古いマクロ可能性があります、コードの実行内容を反映していない可能性がありますが変換する際は注意が必要です。 特に注意が必要、`OPTIONAL`マクロにコメントを頻繁に正しく配置されていないため — たとえば、コンマの間違った側でします。

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

呼び出し元が null ポインターを渡す許可されていない場合に使用して`_In_`または`_Out_`の代わりに`_In_opt_`または`_Out_opt_`です。 これは、そのパラメーターをチェックしは NULL にすることはできないときにエラーが返されますを関数にも適用されます。 正しい防御的なコーディングが予期しない NULL のパラメーターを確認し、適切を返す関数を持つ、限らない、省略可能な型のパラメーターの注釈ができること (`_*Xxx*_opt_`)。

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

## <a name="predefensive-and-postdefensive"></a>\_プレ\_守勢\_と\_Post\_守勢\_

使用することをお勧め関数は、信頼境界に表示されている場合、`_Pre_defensive_`注釈。  「守勢」修飾子があることを示す、呼び出しの時点で特定の注釈を変更、インターフェイスを厳密には、チェックする必要がありますが、実装ボディでそれを想定してください不正確なパラメーターを渡す可能性があります。 その場合は、`_In_ _Pre_defensive_`が信頼の境界を示す、呼び出し元が NULL を渡す開こうとするとエラーが表示されますが、関数本体が分析することパラメーターがあります NULL の場合、最初にポインターを逆参照しようかのように推奨NULL の確認はフラグが付けられます。  A`_Post_defensive_`注釈は、ここで、信頼されたパーティが、呼び出し元であると見なされ、信頼できないコードが呼び出されたコードのコールバックで使用可能でもします。

## <a name="outwrites"></a>\_Out\_書き込みます\_

次の例での一般的な誤用`_Out_writes_`です。

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);

```

注釈`_Out_writes_`バッファーがあることを示します。 `cb`終了時に初期化される最初のバイトを割り当てられたバイト数。 この注釈は厳密に正しくないと、割り当てサイズを表現することをお勧めします。 ただし、示されていない要素の数が、関数によって初期化されます。

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

使用`_Out_ PSTR`が間違っているほとんどの場合。 これは、文字バッファーを指す出力パラメーターを持つものとして解釈されますおよび NULL で終わることをお勧めします。

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);

```

注釈と同様に`_In_ PCSTR`は、一般的で便利です。 あるために、NULL で終わるを入力文字列を指すの precondition`_In_`により、NULL で終わる文字列を認識します。

## <a name="in-wchar-p"></a>\_\_ WCHAR * p

`_In_ WCHAR* p` 入力ポインターがあることを示す`p`1 文字を指しています。 ただし、ほとんどの場合、これはおそらくないものでは、仕様です。 代わりに、NULL で終わる配列; の仕様は、おそらく目的としていますそのために使用`_In_ PWSTR`です。

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);

```

NULL 終了の適切な指定されていませんが一般的です。 使用して、適切な`STR`バージョンを次の例に示すように、型を置き換えます。

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

パラメーターがポインターであり、ポインターは、使用を指していますが、要素の値の範囲を表現する場合`_Deref_out_range_`の代わりに`_Out_range_`です。 次の例の範囲で * pcbFilled を表現すると、pcbFilled されません。

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

 `_Deref_out_range_(0, cbSize)` 不要な厳密に特定のツールから推論することができます`_Out_writes_to_(cbSize,*pcbFilled)`が、完全を期すのためここで表示します。

## <a name="wrong-context-in-when"></a>間違ったコンテキスト\_とき\_

別の一般的なミスは、前提条件の後の状態の評価を使用します。 次の例では、`_Requires_lock_held_`事前条件です。

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);

```

 式`result`前の状態が利用できない状態の後の値を参照します。

## <a name="true-in-success"></a>場合は TRUE\_成功。\_

戻り値が 0 以外の場合、関数が成功した場合を使用して`return != 0`の代わりに、成功条件として`return == TRUE`です。 0 以外が必ずしものコンパイラを提供する実際の値を等価`TRUE`です。 パラメーターを`_Success_`、式は、それと同等として、次の式が評価されます: `return != 0`、 `return != false`、 `return != FALSE`、および`return`なし、パラメーターまたは比較します。

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

参照変数には、以前のバージョンの SAL 注釈の対象として、暗黙的なポインターを使用およびの追加に必要な`__deref`参照変数に接続されている注釈にします。 このバージョン、オブジェクト自体の使用を必要し、しない追加`_Deref_`です。

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

次の例では、戻り値の注釈での一般的な問題を示します。

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();

```

この例では`_Out_opt_`というポインターが前提条件の一部として NULL をする可能性があります。 ただし、前提条件は、戻り値に適用できません。 ここでは、正しい注釈は`_Ret_maybenull_`します。

## <a name="see-also"></a>関連項目

[SAL 注釈を使用して C/C++ のコード障害を減らす](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
[SAL を理解する](../code-quality/understanding-sal.md)
[関数パラメーターおよび戻り値の注釈を付ける](../code-quality/annotating-function-parameters-and-return-values.md)
[関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)
[構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)
[ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)
[注釈を適用するタイミングと場所を指定する](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[の組み込み関数](../code-quality/intrinsic-functions.md)