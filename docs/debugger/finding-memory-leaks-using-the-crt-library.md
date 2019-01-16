---
title: CRT ライブラリを使用したメモリのリークを検出 |Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e29ef610fdfe114525e7da22b58635e0f3e4a3af
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931028"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>CRT ライブラリを使用したメモリ リークの検出

メモリ リークは、C/C++ アプリケーションで最も微妙なと検出が難しいバグです。 結果が正しく割り当てられていたメモリの割り当てを解除する障害からのメモリ リークします。 少量のメモリ リークは最初は、認識されない可能性がありますが、時間の経過と共にパフォーマンスの低下からクラッシュ、アプリのメモリが不足している場合に至るまでの現象が発生できます。 使用可能なメモリを使用して他のアプリがクラッシュを引き起こす可能性のあるリークしているアプリは、混乱したりするアプリを作成します。 さらに無害なメモリ リークには、他の問題を修正する必要がありますを可能性があります。  

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]デバッガーと C ランタイム ライブラリ (CRT) が検出して、メモリ リークを特定できます。  

## <a name="enable-memory-leak-detection"></a>メモリ リークの検出を有効にします。  

メモリ リーク、C と C++ デバッガーと C ランタイム ライブラリ (CRT) を検出するための主要ツールはデバッグ ヒープ関数です。  

すべてのデバッグ ヒープ関数を有効にするには、次の順序で、C++ プログラムで、次のステートメントを含めます。  

```cpp
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  

`#define` ステートメントにより、CRT ヒープ関数の基本バージョンがデバッグ バージョンに対応付けられます。 省略すると、`#define`ステートメントでは、メモリ リーク ダンプがなります[情報](#interpret-the-memory-leak-report)します。  

含む*crtdbg.h*マップ、`malloc`と`free`関数のデバッグ バージョンを[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)と[_free_dbg](/cpp/c-runtime-library/reference/free-dbg)メモリを追跡します。割り当てと解放します。 この対応付けは、 `_DEBUG`が定義されているデバッグ ビルドでだけ行われます。 リリース ビルドでは、通常の `malloc` 関数と `free` 関数が使用されます。  

配置への呼び出しの前のステートメントを使用して、デバッグ ヒープ関数を有効にしたら、 [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)アプリが終了するときに、メモリ リーク レポートを表示するアプリを終了時点より前にします。  

```cpp
_CrtDumpMemoryLeaks();  
```  

手動で配置する必要がありますしない場合は、アプリは、いくつか終了しますがある、`_CrtDumpMemoryLeaks`ですべての終了ポイント。 自動呼び出しが発生する`_CrtDumpMemoryLeaks`各終了時点への呼び出しを配置`_CrtSetDbgFlag`ビット フィールドを次に示しますを使用してアプリの開始時。

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  

既定では、 `_CrtDumpMemoryLeaks` は、メモリ リーク レポートを **[出力]** ウィンドウの **デバッグ** ウィンドウに出力します。 ライブラリを使用すると、情報の出力場所が別の場所に変更されることがあります。 

使用することができます`_CrtSetReportMode`に別の場所にレポートをリダイレクトしたり戻したりする、**出力**次に示すようにウィンドウ。  

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  

## <a name="interpret-the-memory-leak-report"></a>メモリ リーク レポートを解釈します。  

アプリが定義されていない場合`_CRTDBG_MAP_ALLOC`、 [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)次のようなメモリ リーク レポートが表示されます。  

```cmd
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

アプリが定義されている場合`_CRTDBG_MAP_ALLOC`、次のように、メモリ リーク レポート。  

```cmd
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

2 番目のレポートには、リークしたメモリが割り当てられている最初のファイル名と行の番号が表示されます。  

かどうかを定義する`_CRTDBG_MAP_ALLOC`、メモリ リーク レポートが表示されます。  

- これはメモリ割り当て番号`18`の例  
- ブロックの型、`normal`の例です。  
- 16 進数のメモリの場所、`0x00780E80`の例です。  
- ブロックのサイズ`64 bytes`の例です。  
- ブロックのデータの最初の 16 バイト (16 進形式)  

メモリ ブロックの型は*通常*、*クライアント*、または*CRT*します。 *normal ブロック* は、プログラムによって割り当てられる通常のメモリです。 *client ブロック* は、デストラクターを必要とするオブジェクト用に、MFC プログラムが使用する特殊なメモリ ブロックです。 MFC の `new` 演算子は、作成されるオブジェクトに応じて、normal ブロックまたは client ブロックを作成します。 

*CRT ブロック* は、CRT ライブラリが独自に使用するために割り当てるメモリ ブロックです。 CRT ブロックは、CRT ライブラリの重大な問題がある場合を除き、メモリ リーク レポートに表示されませんので、CRT ライブラリは、これらのブロックの割り当て解除を処理します。  

これ以外に、メモリ リーク レポートに表示されないメモリ ブロックが 2 種類あります。 A*空きブロック*メモリがリリースされている定義でリークされていないためです。 *ブロックを無視する*は、メモリ リーク レポートから除外する明示的にマークされているメモリです。  

上記の方法は、標準 CRT を使用して割り当てられたメモリのメモリ リークを特定`malloc`関数。 プログラムが、C++ を使用してメモリを割り当てる場合`new`演算子、ただし、可能性がありますのみが表示されたファイル名および行番号、`operator new`呼び出し`_malloc_dbg`メモリ リーク レポートにします。 さらに便利なメモリ リーク レポートを作成するには、割り当てを行った行を報告するには、次のようなマクロを記述できます。 

```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  

置き換えることができますので、`new`演算子を使用して、`DBG_NEW`コードでマクロ。 デバッグ ビルドで`DBG_NEW`グローバルのオーバー ロードを使用して`operator new`ブロックの型、ファイル、および行番号の追加のパラメーターを受け取る。 オーバー ロード`new`呼び出し`_malloc_dbg`余分な情報を記録します。 メモリ リーク レポートには、リークしたオブジェクトが割り当てられた、ファイル名と行の番号が表示されます。 リリース ビルドも使用して、既定`new`します。 次の手法の例に示します。  

```cpp  
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```  

Visual Studio でこのコードを実行するときにデバッガーへの呼び出し`_CrtDumpMemoryLeaks`でレポートを生成、**出力**次のようなウィンドウ。  

```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  

これは、リークした割り当ての 20 行目がレポートを出力*debug_new.cpp*します。  

>[!NOTE]
>という名前のプリプロセッサ マクロを作成するをお勧めしません`new`、またはその他の言語のキーワード。 

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>メモリ割り当て番号にブレークポイントを設定します。  

メモリ割り当て番号は、リークしているメモリ ブロックがいつ割り当てられたかを示します。 18 のメモリ割り当て番号を持つブロックでは、アプリの実行中に割り当てられたメモリの 18 のブロックなどができます。 CRT レポートでは、CRT ライブラリと MFC などの他のライブラリでの割り当てなど、実行時にメモリ ブロックのすべての割り当てをカウントします。 そのため、メモリ割り当てブロック番号 18 18 に、コードによって割り当てられたメモリ ブロック可能性はありません。 

この割り当て番号を使用して、メモリの割り当てにブレークポイントを設定できます。  

**ウォッチ ウィンドウを使用してメモリ割り当てブレークポイントを設定するには**  

1. アプリの冒頭にあるブレークポイントを設定し、デバッグを開始します。  
   
1. アプリがブレークポイントで一時停止したときに開く、**ウォッチ**ウィンドウを選択して**デバッグ** > **Windows** > **ウォッチ 1**(または**2 を見る**、 **3 を見る**、または**4 を見る**)。  
   
1. **ウォッチ**ウィンドウで、「`_crtBreakAlloc`で、**名前**列。  
   
   マルチ スレッド DLL バージョンの CRT ライブラリ (/MD オプション) を使用している場合は、コンテキスト演算子を追加します。 `{,,ucrtbased.dll}_crtBreakAlloc`  
   
1. **Enter** キーを押します。  
   
   デバッガーによって呼び出しが評価され、その結果が **[値]** 列に表示されます。 メモリ割り当てにまだブレークポイントが設定されていない場合、この値は **-1** になります。  
   
1. **値**列、値をデバッガーが中断するメモリ割り当ての割り当て番号に置き換えます。  

メモリ割り当て番号にブレークポイントを設定した後は、デバッグを続行します。 メモリ割り当て番号が変更されないため、同じ条件下で実行してください。 指定されたメモリの割り当てでプログラムが停止したらを使用して、**呼び出し履歴**ウィンドウとメモリが割り当てられた条件を確認するには、その他のデバッガー ウィンドウ。 次に、オブジェクトの動作を確認する実行を続行し、正常に解放されていない理由ことを確認します。  

オブジェクトにデータ ブレークポイントを設定する方法も役に立つことがあります。 詳細については、「[ブレークポイントの使用](../debugger/using-breakpoints.md)」を参照してください。  

さらに、コード内でメモリ割り当てブレークポイントを設定することもできます。 次のように設定できます。  

```cpp
_crtBreakAlloc = 18;  
```  

 または  

```cpp
_CrtSetBreakAlloc(18);  
```  

## <a name="compare-memory-states"></a>メモリの状態を比較します。  
 メモリ リークの位置を特定するためのもう 1 つの方法では、ある時点におけるアプリケーションのメモリ状態のスナップショットを取得します。 アプリケーションで特定の時点のメモリ状態のスナップショットを実行するには、作成、`_CrtMemState`構造体に渡すと、`_CrtMemCheckpoint`関数。 

```cpp
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
```  

`_CrtMemCheckpoint`関数は、現在のメモリ状態のスナップショットを構造に格納します。  

内容を出力する、`_CrtMemState`構造体、構造体を渡す、`_ CrtMemDumpStatistics`関数。  

```cpp
_CrtMemDumpStatistics( &s1 );  
```  

`_ CrtMemDumpStatistics` 次のようなメモリの状態のダンプが出力されます。  

```cmd
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
```  

コード内のセクションでメモリ リークが発生したかどうかを調べるには、そのセクションの前後のメモリ状態のスナップショットを取得した後、 `_ CrtMemDifference` を使用して 2 つのメモリ状態を比較します。  

```cpp
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  

if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  

`_CrtMemDifference` メモリ状態を比較`s1`と`s2`で結果を返します (`s3`) 間の差は`s1`と`s2`します。  

配置することでメモリ リークを検索するための 1 つの方法は、まず`_CrtMemCheckpoint`先頭と末尾を使用して、アプリの呼び出し`_CrtMemDifference`結果を比較します。 場合`_CrtMemDifference`さらに追加することができます、メモリ リークを示しています`_CrtMemCheckpoint`呼び出しまで、リークの原因を分離している場合、バイナリ検索を使用してプログラムを分割します。  

## <a name="false-positives"></a>誤検知  
 `_CrtDumpMemoryLeaks` ライブラリは、CRT ブロックまたはクライアントのブロックではなく通常のブロックとして内部の割り当てをマークした場合、メモリ リークの兆候が false を指定できます。 その場合、 `_CrtDumpMemoryLeaks` では、ユーザー割り当てとライブラリの内部的な割り当てを区別することができません。 ライブラリ割り当てのグローバル デストラクターが、 `_CrtDumpMemoryLeaks`の呼び出しポイント後に実行される場合、すべての内部ライブラリ割り当てがメモリ リークとして報告されます。 標準テンプレート ライブラリを Visual Studio .NET が発生する可能性がありますよりも前のバージョン`_CrtDumpMemoryLeaks`このような誤検知を報告します。  

## <a name="see-also"></a>関連項目  
 [CRT デバッグ ヒープの詳細](../debugger/crt-debug-heap-details.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)
