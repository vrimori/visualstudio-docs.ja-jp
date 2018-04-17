---
title: CRT ライブラリを使用してメモリ リークの検出 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: c02fea4639d130840f3f5dbbd9e77693c676d304
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>CRT ライブラリを使用したメモリ リークの検出
メモリ リークとは、割り当て済みのメモリを適切に解放できない状態を指します。メモリ リークは、C/C++ アプリケーションで最も微妙で検出しにくいバグの 1 つです。 わずかなメモリ リークは最初は認識されないことがありますが、長期にわたる累積的なメモリ リークによりアプリケーションがメモリ不足になると、パフォーマンスの低下からクラッシュまで、さまざまな兆候が現れる可能性があります。 さらに悪い状況として、メモリ リークしているアプリケーションによってすべての使用可能なメモリが消費されると、別のアプリケーションがクラッシュし、原因となったアプリケーションの特定が困難になることもあります。 一見問題にならないように思われるメモリ リークであっても、修正が必要な別の問題につながっている可能性があります。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデバッガーと C ランタイム (CRT) ライブラリには、メモリ リークを検出および識別するための効率的な手段が用意されています。  
  
## <a name="enabling-memory-leak-detection"></a>メモリ リーク検出の有効化  
 メモリ リークを検出するための主要ツールは、デバッガーと C ランタイム ライブラリ (CRT) デバッグ ヒープ関数です。  
  
 デバッグ ヒープ関数を有効にするには、次のステートメントをプログラムに追加します。  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 CRT 関数を正常に機能させるには、ここに示した順序で `#include` ステートメントを定義する必要があります。  
  
 crtdbg.h をインクルードすると、 `malloc` 関数と [free](/cpp/c-runtime-library/reference/free) 関数は、それぞれのデバッグ バージョンである [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) と `free`に対応付けられます。これらの関数では、メモリの割り当てと解放が追跡されます。 この対応付けは、 `_DEBUG`が定義されているデバッグ ビルドでだけ行われます。 リリース ビルドでは、通常の `malloc` 関数と `free` 関数が使用されます。  
  
 `#define` ステートメントにより、CRT ヒープ関数の基本バージョンがデバッグ バージョンに対応付けられます。 `#define` ステートメントを省略した場合、メモリ リーク ダンプに含まれる情報が少なくなります。  
  
 これらのステートメントを使用してデバッグ ヒープ関数を有効にした後、アプリケーションの終了ポイントの前に `_CrtDumpMemoryLeaks` の呼び出しを配置すると、アプリケーションの終了時にメモリ リーク レポートを表示できます。  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 アプリケーションの終了ポイントが複数ある場合、すべての終了ポイントに手動で [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) の呼び出しを配置する必要はありません。 アプリケーションの先頭で `_CrtSetDbgFlag` を呼び出すと、各終了ポイントで自動的に `_CrtDumpMemoryLeaks` が呼び出されるようになります。 次に示す 2 つのビット フィールドを設定する必要があります。  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 既定では、 `_CrtDumpMemoryLeaks` は、メモリ リーク レポートを **[出力]** ウィンドウの **デバッグ** ウィンドウに出力します。 レポートを別の場所にリダイレクトするには、 `_CrtSetReportMode` を使用します。  
  
 ライブラリを使用すると、情報の出力場所が別の場所に変更されることがあります。 この場合は、次の方法で出力先を **[出力]** ウィンドウに戻すことができます。  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>メモリ リーク レポートの解釈  
 アプリケーションで `_CRTDBG_MAP_ALLOC`を定義していない場合は、 [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) により次のようなメモリ リーク レポートが出力されます。  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 アプリケーションで `_CRTDBG_MAP_ALLOC`を定義している場合は、次のようなメモリ リーク レポートが出力されます。  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 これらの違いとして、2 つ目のレポートには、リークしているメモリが最初に割り当てられたファイルと行番号が表示されます。  
  
 `_CRTDBG_MAP_ALLOC` を定義するかどうかにかかわらず、メモリ リーク レポートには次の情報が表示されます。  
  
-   メモリの割り当て番号 (この例では " `18` ")  
  
-   [ブロックの型](http://msdn.microsoft.com/en-us/e2f42faf-0687-49e7-aa1f-916038354f97)(この例では " `normal` ")  
  
-   16 進形式で表したメモリ位置 (この例では " `0x00780E80` ")  
  
-   ブロックのサイズ (この例では " `64 bytes` ")  
  
-   ブロックのデータの最初の 16 バイト (16 進形式)  
  
 メモリ リーク レポートでは、メモリ ブロックは normal、client、または CRT として識別されます。 *normal ブロック* は、プログラムによって割り当てられる通常のメモリです。 *client ブロック* は、デストラクターを必要とするオブジェクト用に、MFC プログラムが使用する特殊なメモリ ブロックです。 MFC の `new` 演算子は、作成されるオブジェクトに応じて、normal ブロックまたは client ブロックを作成します。 *CRT ブロック* は、CRT ライブラリが独自に使用するために割り当てるメモリ ブロックです。 これらのブロックの解放処理は CRT ライブラリが行います。 したがって、重大な問題 (CRT ライブラリの破損など) があるとき以外は、これらがメモリ リーク レポートに表示されることはありません。  
  
 これ以外に、メモリ リーク レポートに表示されないメモリ ブロックが 2 種類あります。 *free ブロック* は、解放済みのメモリ ブロックです。 つまり、名前が示すとおり、リークは発生していません。 *ignore ブロック* は、メモリ リーク レポートに出力しないように明示的にマークされているブロックです。  
  
 これらの手法は、標準 CRT の `malloc` 関数を使用して割り当てられたメモリに適用されます。 場合は、プログラムは、C++ を使用してメモリを割り当てます`new`演算子、ただし、のみが表示ファイルと行番号、グローバルの実装`operator new`呼び出し`_malloc_dbg`メモリ リーク レポートにします。 その動作はあまり役に立ちません、ためには、次のようなマクロを使用して、割り当てが行われた行を報告するようを変更できます。 
 
```C++  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
これで、置き換えることができます、`new`演算子を使用して、`DBG_NEW`コード内のマクロです。 デバッグ ビルドで、これは、使用するオーバー ロードのグローバル`operator new`ブロックの型、ファイル、および行番号の追加のパラメーターを取得します。 このオーバー ロード`new`呼び出し`_malloc_dbg`余分な情報を記録します。 使用すると`DBG_NEW`、メモリ リーク レポートがリークしているオブジェクトが割り当てられているファイル名と行番号が表示されます。 既定値を使用して、製品版ビルドで`new`です。 (お勧めしませんという名前のプリプロセッサ マクロを作成する`new`、またはその他の言語のキーワードです)。方法の例を次に示します。  
  
```C++  
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
  
Visual Studio への呼び出しで、デバッガーでこのコードを実行すると`_CrtDumpMemoryLeaks`でレポートを生成、**出力**次のようにウィンドウ。  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
漏洩した割り当て debug_new.cpp の 20 行目がこれが示しています。  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>メモリ割り当て番号へのブレークポイントの設定  
 メモリ割り当て番号は、リークしているメモリ ブロックがいつ割り当てられたかを示します。 たとえば、メモリ割り当て番号が 18 のブロックは、アプリケーションの実行中に割り当てられたメモリの 18 番目のブロックです。 CRT レポートでは、実行中のすべてのメモリ ブロック割り当てがカウントされます。 これには、CRT ライブラリおよびその他のライブラリ (MFC など) による割り当ても含まれます。 したがって、メモリ割り当て番号が 18 のブロックは、コードによって 18 番目に割り当てられたブロックであるとは限りません。 そして、通常はそうではありません。  
  
 この割り当て番号を使用して、メモリの割り当てにブレークポイントを設定できます。  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>ウォッチ ウィンドウを使用してメモリ割り当てブレークポイントを設定するには  
  
1.  アプリケーションの先頭付近にブレークポイントを設定し、アプリケーションを起動します。  
  
2.  アプリケーションがブレークポイントで停止したら、 **ウォッチ** ウィンドウに移動します。  
  
3.  **ウォッチ** ウィンドウの `_crtBreakAlloc` [名前] **列に、「** 」と入力します。  
  
     マルチスレッド DLL バージョン (/MD オプション) の CRT ライブラリを使用している場合は、コンテキスト演算子を追加して「 `{,,ucrtbased.dll}_crtBreakAlloc`」とします。  
  
4.  **RETURN**キーを押します。  
  
     デバッガーによって呼び出しが評価され、その結果が **[値]** 列に表示されます。 メモリ割り当てにブレークポイントを設定していない場合は、この値を-1 になります。  
  
5.  **[値]** 列の値を、ブレークポイントを設定するメモリ割り当ての割り当て番号に置き換えます。  
  
 メモリ割り当て番号にブレークポイントを設定したら、デバッグを続行できます。 メモリ割り当ての順序が変わらないように、前回実行したときと同じ条件でプログラムを実行してください。 指定したメモリ割り当てでプログラムが停止したら、 **[呼び出し履歴]** ウィンドウやその他のデバッガー ウィンドウを参照して、メモリが割り当てられた状況を確認できます。 その後、実行を続行して、オブジェクトで何が起こっているかを確認し、オブジェクトが正常に解放されない原因を調べることができます。  
  
 オブジェクトにデータ ブレークポイントを設定する方法も役に立つことがあります。 詳細については、「 [Using Breakpoints](../debugger/using-breakpoints.md)」を参照してください。  
  
 さらに、コード内でメモリ割り当てブレークポイントを設定することもできます。 これには、2 つの方法があります。  
  
```  
_crtBreakAlloc = 18;  
```  
  
 または  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>メモリ状態の比較  
 メモリ リークの位置を特定するためのもう 1 つの方法では、ある時点におけるアプリケーションのメモリ状態のスナップショットを取得します。 アプリケーションの任意の時点でのメモリ状態のスナップショットを取得するには、 **_CrtMemState** 構造体を作成し、 `_CrtMemCheckpoint` 関数に渡します。 この関数は、現在のメモリ状態のスナップショットを構造体に格納します。  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` は、現在のメモリ状態のスナップショットを構造体に格納します。  
  
 **_CrtMemState** 構造体の内容を出力するには、構造体を `_ CrtMemDumpStatistics` 関数に渡します。  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` は、メモリ状態のダンプを出力します。次に例を示します。  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 コード内のセクションでメモリ リークが発生したかどうかを調べるには、そのセクションの前後のメモリ状態のスナップショットを取得した後、 `_ CrtMemDifference` を使用して 2 つのメモリ状態を比較します。  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` は、 `s1` と `s2` のメモリ状態を比較し、結果を`s3`に返します。これが `s1` と `s2`の相違となります。  
  
 メモリ リークを見つけるための 1 つの方法では、最初にアプリケーションの先頭と末尾で `_CrtMemCheckpoint` を呼び出し、`_CrtMemDifference` を使用して結果を比較します。 `_CrtMemDifference` によってメモリ リークが示された場合は、さらに多くの `_CrtMemCheckpoint` の呼び出しを追加して、リークの原因が特定されるまでバイナリ サーチを使用してプログラムを分割できます。  
  
## <a name="false-positives"></a>誤検知  
 場合により、 `_CrtDumpMemoryLeaks` は実際にはメモリ リークでないにもかかわらず、メモリ リークを報告することがあります。 これは、内部的な割り当てを `_CRT_BLOCK`や `_CLIENT_BLOCK`としてマークせず、_NORMAL_BLOCK としてマークするライブラリを使用した場合に発生することがあります。 その場合、 `_CrtDumpMemoryLeaks` では、ユーザー割り当てとライブラリの内部的な割り当てを区別することができません。 ライブラリ割り当てのグローバル デストラクターが、 `_CrtDumpMemoryLeaks`の呼び出しポイント後に実行される場合、すべての内部ライブラリ割り当てがメモリ リークとして報告されます。 Visual Studio .NET より前のバージョンの標準テンプレート ライブラリは、 `_CrtDumpMemoryLeaks` が誤検出を報告する原因となっていましたが、最近のリリースでは修正されています。  
  
## <a name="see-also"></a>関連項目  
 [CRT デバッグ ヒープ](../debugger/crt-debug-heap-details.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)
