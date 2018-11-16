---
title: CRT デバッグ ヒープの詳細 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 691db8ce3b9b956ef7e0299acddac74c926fcf5a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803020"
---
# <a name="crt-debug-heap-details"></a>CRT デバッグ ヒープ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックでは、CRT デバッグ ヒープについて詳しく解説します。  
  
##  <a name="BKMK_Contents"></a> 目次  
 [デバッグ ヒープを使用してバッファー オーバーランを見つける](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [デバッグ ヒープ上のブロックの型](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [ヒープの整合性とメモリ リーク チェック](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [デバッグ ヒープを構成します。](#BKMK_Configure_the_debug_heap)  
  
 [new、delete、_client_block、C++ のデバッグ ヒープ](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [ヒープ状態レポート関数](#BKMK_Heap_State_Reporting_Functions)  
  
 [ヒープ割り当て要求を追跡します。](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> デバッグ ヒープを使用してバッファー オーバーランを見つける  
 割り当てたバッファーの末尾を超えて書き込みをしてしまうこと、およびメモリ リーク (不要になったメモリ割り当てを解放し忘れること) は、プログラマが経験する問題の中で最も一般的でありながら、最もやっかいなものです。 デバッグ ヒープは、このようなメモリ割り当ての問題を解決するための強力なツールとなります。  
  
 デバッグ バージョンのヒープ関数は、リリース ビルドで使用される標準バージョン (基本バージョン) の関数を呼び出します。 メモリ ブロックの割り当てが要求されると、デバッグ ヒープ マネージャーは、要求されたサイズより少し大きめのメモリ ブロックをベース ヒープから割り当て、このブロック内のユーザー領域へのポインターを返します。 たとえば、アプリケーション中で `malloc( 10 )` という呼び出しをしたとします。 リリース ビルドで[malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0)は 10 バイトの割り当てを要求のベース ヒープ割り当てルーチンを呼び出します。 ただし、デバッグ ビルドで`malloc`呼び出して[_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)、10 バイトの割り当てと、追加のメモリの約 36 バイト加えた要求ベース ヒープ割り当てルーチンを呼び出します。 デバッグ ヒープに割り当てられたすべてのメモリ ブロックは、単一のリンク リストとして、割り当てられた順番で連結されます。  
  
 デバッグ ヒープ ルーチンによって余分に割り当てられたメモリは、ブックキーピング情報や、デバッグ用のメモリ ブロックを連結するためのポインター用に使用されます。また、割り当てられた領域を超えて行われた書き込みを検出するために割り当て領域の前後に確保される小さなバッファーとしても使用されます。  
  
 現在、デバッグ ヒープ用のブックキーピング情報を格納するために使用されるブロック ヘッダー構造体は、DBGINT.H ヘッダー ファイルで次のように宣言されています。  
  
```  
typedef struct _CrtMemBlockHeader  
{  
// Pointer to the block allocated just before this one:  
    struct _CrtMemBlockHeader *pBlockHeaderNext;  
// Pointer to the block allocated just after this one:  
    struct _CrtMemBlockHeader *pBlockHeaderPrev;  
    char *szFileName;    // File name  
    int nLine;           // Line number  
    size_t nDataSize;    // Size of user block  
    int nBlockUse;       // Type of block  
    long lRequest;       // Allocation number  
// Buffer just before (lower than) the user's memory:  
    unsigned char gap[nNoMansLandSize];  
} _CrtMemBlockHeader;  
  
/* In an actual memory block in the debug heap,  
 * this structure is followed by:  
 *   unsigned char data[nDataSize];  
 *   unsigned char anotherGap[nNoMansLandSize];  
 */  
```  
  
 `NoMansLand`ブロックのユーザーのデータ領域の両側のバッファー サイズは、4 バイトでは現在、メモリ ブロックのユーザーの制限が上書きされないことを確認する、デバッグ ヒープ ルーチンによって使用される既知のバイト値が格納されます。 デバッグ ヒープは、新しく確保されたメモリ ブロックにも既知の値を格納します。 解放されたブロックをヒープのリンク リストに保持するように設定した場合は、解放済みのブロックにも既知の値が格納されます。 現在、実際に使用されているバイト値は次のとおりです。  
  
 NoMansLand (0xFD)  
 アプリケーションが使用するメモリ領域の前後に確保される "NoMansLand" バッファーには 0xFD が格納されます。  
  
 解放済みのブロック (0xDD)  
 `_CRTDBG_DELAY_FREE_MEM_DF` フラグが設定されている場合、解放済みのブロックは使用されずにヒープのリンク リストに保持され、0xDD が格納されます。  
  
 新規オブジェクト (0xCD)  
 新規オブジェクトには、メモリの割り当て時に 0xCD が格納されます。  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop")  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> デバッグ ヒープ上のブロックの型  
 デバッグ ヒープ上のすべてのメモリ ブロックには、5 つの割り当て型のうちのいずれかの型が割り当てられます。 型によって、メモリ リークの検出やメモリ状態をレポートするときの追跡方法やレポート方法が異なります。 ブロックの型を指定するには、デバッグ ヒープ割り当て関数の 1 つの直接呼び出しをなどを使用して割り当てることによって[_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)します。 デバッグ ヒープ内のメモリ ブロックの 5 つの種類 (で設定、 **nBlockUse**のメンバー、**示します**構造) 次に示します。  
  
 **_NORMAL_BLOCK**  
 呼び出し[malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0)または[calloc](http://msdn.microsoft.com/library/17bb79a1-98cf-4096-90cb-1f9365cd6829) Normal ブロックを作成します。 Normal ブロックだけを使用して、クライアントのブロックのない必要とする場合は、定義たい[_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b)、デバッグ ビルドでのデバッグ バージョンにマップするこれにより、すべてのヒープ割り当てを呼び出します。 これによって、ヒープ割り当て関数の呼び出しに関連するファイル名と行番号情報を対応するブロック ヘッダーに格納できます。  
  
 `_CRT_BLOCK`  
 多数のランタイム ライブラリ関数は、内部的にメモリ ブロックを割り当てます。このように内部的に割り当てられたメモリ ブロックは CRT ブロックとして個別に扱われます。 そのため、メモリ リークの検出などの処理には、これらのブロックは影響しません。 CRT 型のブロックが、割り当て関数によって割り当てられたり、再割り当てされたり、解放されたりすることはありません。  
  
 `_CLIENT_BLOCK`  
 アプリケーションでは、デバッグ ヒープ関数を明示的に呼び出し、このメモリ ブロック型を割り当てることによって、特定の割り当て領域をデバッグの目的で特別に追跡できます。 MFC では、すべて割り当てなど、 **Cobject**クライアントのブロックとして他のアプリケーションは、クライアントのブロックでさまざまなメモリ オブジェクトを保持可能性があります。 より細かい追跡を実施するために、Client ブロック型を細分化することもできます。 Client ブロック型を細分化した型を指定するには、その型を表す数値を左に 16 ビットシフトし、`OR` との `_CLIENT_BLOCK` 演算を行います。 例えば:  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 使用してクライアントのブロック単位で格納されているオブジェクトをダンプするためのクライアントが指定したフック関数をインストールできる[_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033)、デバッグ関数によって、クライアントのブロックをダンプするたびに、呼び出されるとします。 また、 [_CrtDoForAllClientObjects](http://msdn.microsoft.com/library/d0fdb835-3cdc-45f1-9a21-54208e8df248)デバッグ ヒープ内の各 Client ブロック用のアプリケーションによって提供される特定の関数の呼び出しに使用できます。  
  
 **_FREE_BLOCK**  
 通常は解放済みのブロックはリストから削除されます。 ただし、解放済みのメモリに書き込みが行われていないかどうかをチェックしたり、メモリ不足の状態をシミュレートしたりするために、解放されたブロックをリンク リストに残しておくこともできます。その場合は、解放されていることを示すために、既知のバイト値 (現在は 0xDD) が格納されます。  
  
 **_IGNORE_BLOCK**  
 デバッグ ヒープ処理を一定期間だけオフにできます。 この間は、メモリ ブロックはリスト中に保持されますが、Ignore ブロックとしてマークされます。  
  
 タイプとサブタイプの所定のブロックを確認するのには、関数を使用して[_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)とマクロ **_BLOCK_TYPE**と **_BLOCK_SUBTYPE**します。 これらのマクロは、crtdbg.h で次のように定義されています。  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> ヒープの整合性とメモリ リーク チェック  
 デバッグ ヒープ用の機能の多くは、コードの中からアクセスする必要があります。 次のセクションでは、これらの機能のいくつかについて、使用方法を説明します。  
  
 `_CrtCheckMemory`  
 呼び出しを使用する[_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765)など、任意の時点で、ヒープの整合性をチェックします。 この関数は、ヒープ上の各メモリ ブロックを検査し、メモリ ブロックのヘッダー情報が有効かどうかを検証すると同時にバッファーが変更されていないかどうかを確認します。  
  
 `_CrtSetDbgFlag`  
 デバッグ ヒープの追跡方法、内部のフラグを使用して割り当てを制御できます[_crtDbgFlag](http://msdn.microsoft.com/library/9e7adb47-8ab9-4e19-81d5-e2f237979973)、読み取りを使用して設定できますが、 [_CrtSetDbgFlag](http://msdn.microsoft.com/library/b5657ffb-6178-4cbf-9886-1af904ede94c)関数。 このフラグを変更することによって、デバッグ ヒープを使用して、プログラムの終了時にメモリ リークをチェックし、検出されたメモリ リークをすべて出力できます。 同様に、解放されたメモリ ブロックをリンク リストから削除しないよう指定することによって、メモリ不足の状態をシミュレートすることもできます。 ヒープのチェック時には、解放されたメモリ ブロックがそのままの状態で維持されているかどうかを確認します。  
  
 **_CrtDbgFlag**フラグには、次のビット フィールドが含まれています。  
  
|ビット フィールド|既定値<br /><br /> 値|説明|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|オン|デバッグ用の割り当てをオンにします。 チェーン化されたときにこのビットがオフ、割り当てがそのブロック型は **_IGNORE_BLOCK**します。|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|オフ|メモリ不足の状態をシミュレートできるように、実際にはメモリを解放しません。 解放されたブロックがデバッグ ヒープのリンク リストに保持されますとマークされてこのビットがオンの **_FREE_BLOCK**特別なバイト値が設定されます。|  
|**_CRTDBG_CHECK_ALWAYS_DF**|オフ|により **_CrtCheckMemory**ごとの割り当てと割り当て解除時に呼び出されます。 実行速度は遅くなりますが、エラーをすばやく検出できます。|  
|**_CRTDBG_CHECK_CRT_DF**|オフ|ブロックの型としてマークされている **_CRT_BLOCK**リークの検出と状態の差分の操作に含まれます。 このビットがオフの場合、ランタイム ライブラリによって内部的に使用されるメモリは、これらの処理対象には含まれません。|  
|**_CRTDBG_LEAK_CHECK_DF**|オフ|メモリ リークをへの呼び出しを使用してプログラムの終了時に実行されるチェック **_CrtDumpMemoryLeaks**します。 アプリケーションが割り当てたメモリを解放できていない場合は、エラー レポートが生成されます。|  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> デバッグ ヒープを構成します。  
 `malloc`、`free`、`calloc`、`realloc`、`new`、`delete` などのヒープ関数の呼び出しは、すべてデバッグ ヒープで動作するデバッグ バージョンのヒープ関数に置き換えられます。 メモリ ブロックが解放されると、デバッグ ヒープは割り当て領域の前後に確保されたバッファーが完全かどうかを自動的にチェックし、それらのバッファーが上書きされていた場合はエラーを出力します。  
  
 **デバッグ ヒープを使用するには**  
  
- アプリケーションのデバッグ ビルドに C ランタイム ライブラリのデバッグ バージョンをリンクします。  
  
  **1 つまたは複数の _crtDbgFlag ビット フィールドを変更し、フラグの新しい状態を作成するには**  
  
1. `_CrtSetDbgFlag` パラメーターに `newFlag` を設定して `_CRTDBG_REPORT_FLAG` を呼び出すことによって、現在の `_crtDbgFlag` の状態を取得し、その値を一時変数に格納します。  
  
2. ビットをオンにする`OR`- ing (ビットごと&#124;シンボル)、一時変数 (のマニフェスト定数によってアプリケーション コードで表される)、対応するビットマスクを使用します。  
  
3. 一時変数と、オフにするビットマスクの `AND` (ビット演算子の ~) との `NOT` (ビット演算子の &) をとることで、ビットをオフにします。  
  
4. `_CrtSetDbgFlag` パラメーターに一時変数に格納されている値を設定して `newFlag` を呼び出すことによって、`_crtDbgFlag` の新しい状態を作成します。  
  
   たとえば、次のコードは、メモリ リークの自動検出をオンにし、`_CRT_BLOCK` 型のブロックに関するチェックをオフにします。  
  
```  
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> new、delete、_client_block、C++ のデバッグ ヒープ  
 C ランタイム ライブラリのデバッグ バージョンには、C++ の `new` 演算子と `delete` 演算子のデバッグ バージョンが含まれています。 `_CLIENT_BLOCK` 型を割り当てる場合は、次の例に示すように、`new` 演算子のデバッグ バージョンを直接呼び出すか、デバッグ モードで `new` 演算子を置き換えるマクロを作成する必要があります。  
  
```  
/* MyDbgNew.h  
 Defines global operator new to allocate from  
 client blocks  
*/  
  
#ifdef _DEBUG  
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)  
#else  
   #define DEBUG_CLIENTBLOCK  
#endif // _DEBUG  
  
/* MyApp.cpp  
        Use a default workspace for a Console Application to  
 *      build a Debug version of this code  
*/  
  
#include "crtdbg.h"  
#include "mydbgnew.h"  
  
#ifdef _DEBUG  
#define new DEBUG_CLIENTBLOCK  
#endif  
  
int main( )   {  
    char *p1;  
    p1 =  new char[40];  
    _CrtMemDumpAllObjectsSince( NULL );  
}  
```  
  
 デバッグ バージョンの `delete` 演算子は、すべてのブロック型に対して使用できるため、リリース バージョンのコンパイル時にプログラムを変更する必要はありません。  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> ヒープ状態レポート関数  
 **_CrtMemState**  
  
 ある時点でのヒープの状態のスナップショットを取得するには、CRTDBG.H で定義されている _CrtMemState 構造体を使用します。  
  
```  
typedef struct _CrtMemState  
{  
    // Pointer to the most recently allocated block:  
    struct _CrtMemBlockHeader * pBlockHeader;  
    // A counter for each of the 5 types of block:  
    size_t lCounts[_MAX_BLOCKS];  
    // Total bytes allocated in each block type:  
    size_t lSizes[_MAX_BLOCKS];  
    // The most bytes allocated at a time up to now:  
    size_t lHighWaterCount;  
    // The total bytes allocated at present:  
    size_t lTotalCount;  
} _CrtMemState;  
```  
  
 この構造体には、デバッグ ヒープのリンク リストの先頭 (最近割り当てられた) ブロックへのポインターが格納されます。 次の 2 つの配列には、リスト内にある各メモリ ブロック型 (_NORMAL_BLOCK、`_CLIENT_BLOCK`、_FREE_BLOCK など) の個数と、各ブロック型に割り当てられているバイト数が格納されています。 最後に、その時点までにヒープに割り当てられたバイト数の最大値と、現在割り当てられているバイト数が格納されています。  
  
 **その他の CRT をレポートする関数**  
  
 ヒープの状態と内容をレポートするための関数を次に示します。これらの関数によって取得した情報を利用して、メモリ リークなどの問題を検出できます。  
  
|関数|説明|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](http://msdn.microsoft.com/library/f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc)|内のヒープのスナップショットを保存、 **_CrtMemState**アプリケーションによって提供される構造体。|  
|[_CrtMemDifference](http://msdn.microsoft.com/library/0f327278-b551-482f-958b-76941f796ba4)|メモリ状態を格納した 2 つの構造体を比較し、その相違点を別の構造体に保存します。2 つの状態が異なっている場合は TRUE を返します。|  
|[_CrtMemDumpStatistics](http://msdn.microsoft.com/library/27b9d731-3184-4a2d-b9a7-6566ab28a9fe)|ダンプを特定 **_CrtMemState**構造体。 この構造体には、ある時点でのデバッグ ヒープの状態のスナップショット、または 2 つのスナップショットの相違点が格納されています。|  
|[_CrtMemDumpAllObjectsSince](http://msdn.microsoft.com/library/c48a447a-e6bb-475c-9271-a3021182a0dc)|指定されたスナップショットの取得以降、またはプログラムの実行開始以降に割り当てられたすべてのオブジェクトに関する情報をダンプします。 ダンプするたびに、 **_CLIENT_BLOCK**ブロックを使用して 1 つインストールされている場合は、アプリケーションによって提供されるフック関数を呼び出して **_CrtSetDumpClient**します。|  
|[_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c)|プログラムの実行開始以降にメモリ リークが発生したかどうかを調べます。メモリ リークが発生している場合は、割り当てられている全オブジェクトをダンプします。 毎回 **_CrtDumpMemoryLeaks**ダンプ、 **_CLIENT_BLOCK**ブロックを使用して 1 つインストールされている場合は、アプリケーションによって提供されるフック関数を呼び出す **_CrtSetDumpClient**.|  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> ヒープ割り当て要求を追跡します。  
 アサート マクロやレポート マクロの場合は、それらが実行されたソース ファイル名や行番号を特定することが、問題の原因となっている場所を突き止めるためにたいへん役に立ちますが、これはヒープ割り当て関数には当てはまりません。 マクロはアプリケーションの論理ツリー内で適切な位置に挿入されますが、ヒープの割り当ては、さまざまな時点でさまざまな場所から呼び出される特殊なルーチンの中に埋もれていることが多いためです。 通常は、不正なヒープ割り当てがコードのどの行で発生しているかではなく、その行で行われる膨大なヒープ割り当てのうち、どの割り当てが、どのような理由で不正になるかということが問題となります。  
  
 **一意の割り当て要求番号と _crtBreakAlloc**  
  
 不正となるヒープ割り当て呼び出しを特定するには、デバッグ ヒープ上の各ブロックに関連付けられている一意の割り当て要求番号を利用する方法が最も簡単です。 この割り当て要求番号がかっこで囲まれたブロックに関する情報がダンプ関数のいずれかによって報告された場合 (たとえば、"{36}")。  
  
 不適切に割り当てられたブロックの割り当て要求番号がわかれば、渡すことができますこの数を[_CrtSetBreakAlloc](http://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1)ブレークポイントを作成します。 このブロックが割り当てられる直前でプログラムの実行が停止するため、その時点からさかのぼって、不正な呼び出しの原因となっているルーチンを突き止めることができます。 再コンパイルを避けるためを設定してデバッガーで同じ処理を行うことができます **_crtBreakAlloc**興味のある割り当て要求番号にします。  
  
 **独自割り当てルーチンのデバッグ バージョンを作成します。**  
  
 複雑なアプローチと同等に、独自割り当てルーチンのデバッグ バージョンを作成する、 **_dbg**のバージョン、[ヒープ割り当て関数](../debugger/debug-versions-of-heap-allocation-functions.md)します。 そして、基本のヒープ割り当てルーチンにソース ファイルと行番号を引数として渡します。こうすると、不正な割り当てが発生した場所をすばやく見つけることができます。  
  
 たとえば、アプリケーションに次のような共用ルーチンがあるとします。  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 ヘッダー ファイルに、次のようなコードを追加します。  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 次に、レコード作成ルーチンによる割り当てを次のように変更します。  
  
```  
int addNewRecord(struct RecStruct *prevRecord,  
                int recType, int recAccess  
#ifdef _DEBUG  
               , const char *srcFile, int srcLine  
#endif  
    )  
{  
    /* ... code omitted through actual allocation ... */  
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,  
            srcFile, scrLine)) == NULL)  
    /* ... rest of routine omitted too ... */  
}  
```  
  
 これで、`addNewRecord` が呼び出された場所のソース ファイル名と行番号が、デバッグ ヒープ上に割り当てられた各ブロックに格納されるため、このブロックを調べれば、これらの情報を出力できます。  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)



