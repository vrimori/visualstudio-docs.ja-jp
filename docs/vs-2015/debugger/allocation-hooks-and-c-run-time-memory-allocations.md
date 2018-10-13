---
title: 割り当てフック関数と C ランタイムのメモリの割り当て |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22856782fb8d0ad92a19f03c7c3a474763310a60
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273716"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>割り当てフック関数と C ランタイムのメモリ割り当て
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

メモリ割り当て用のフック関数には重要な制限事項があります。それは、メモリを内部的に割り当てるタイプの C ランタイム ライブラリ関数をフック関数から呼び出す場合、`_CRT_BLOCK` 型のブロック (C ランタイム ライブラリ関数によって内部的に割り当てられるメモリ) を明示的に無視する必要があることです。 割り当て用のフック関数の先頭に次のようなコードを追加すると、`_CRT_BLOCK` 型のブロックを無視できます。  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 割り当て用のフック関数で `_CRT_BLOCK` 型のブロックを無視しないと、このフック関数から C ランタイム ライブラリ関数を呼び出した場合に、プログラムが無限ループに陥ることがあります。 たとえば、`printf` は内部的にメモリを割り当てます。 フック、コードから呼び出す場合`printf`、呼び出しは、もう一度呼び出すフック関数と、その結果の割り当てし、 **printf** 、もう一度まで、スタック オーバーフローが発生します。 `_CRT_BLOCK` 型の割り当て処理をレポートする必要がある場合は、この制限事項を回避するために、C ランタイム関数ではなく Windows API 関数を使用して書式設定や出力を行う方法があります。 Windows API は C ランタイム ライブラリのヒープを使用しないため、割り当て用のフック関数を使用しても無限ループに陥る心配はありません。  
  
 ランタイム ライブラリのソース ファイルを調べると場合、表示されます、既定の割り当てフック関数を**CrtDefaultAllocHook** (単に返す**TRUE**)、独自の個別のファイルにあります。DBGHOOK します。C. 割り当てフック関数、アプリケーションの前に実行されるランタイム スタートアップ コードで行われた割り当ての場合でも呼び出す場合**メイン**関数の代わりに、独自のいずれかでこの既定の関数を置き換えることができます使用して[_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d)します。  
  
## <a name="see-also"></a>関連項目  
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 サンプル](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



