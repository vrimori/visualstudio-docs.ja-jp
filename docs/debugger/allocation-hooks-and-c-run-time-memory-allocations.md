---
title: 割り当てフック関数と C ランタイムのメモリの割り当て |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e4c631b72ae9b12f77daf2ddd49919651c0b3e5
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433107"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>割り当てフック関数と C ランタイムのメモリ割り当て
割り当てフック関数の非常に重要な制限は、無視する必要があります明示的に`_CRT_BLOCK`ブロックします。 これらのブロックは、内部のメモリを割り当てる C ランタイム ライブラリ関数を呼び出す場合、C ランタイム ライブラリ関数によって内部的に行われたメモリ割り当てです。 無視してかまいません`_CRT_BLOCK`割り当ての先頭に folloiwng コードを含めることによってブロックが関数をフックします。  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 割り当てフック関数を無視しない場合`_CRT_BLOCK`フックで呼び出される C ランタイム ライブラリ関数が無限ループにプログラムをトラップし、ブロックします。 たとえば、`printf` は内部的にメモリを割り当てます。 フック、コードから呼び出す場合`printf`、呼び出しは、もう一度呼び出すフック関数と、その結果の割り当てし、 **printf**で、もう一度まで、スタック オーバーフローが発生します。 `_CRT_BLOCK` 型の割り当て処理をレポートする必要がある場合は、この制限事項を回避するために、C ランタイム関数ではなく Windows API 関数を使用して書式設定や出力を行う方法があります。 Windows Api では、C ランタイム ライブラリのヒープを使用しないために、無限ループで、割り当てフックをトラップされません。  
  
 ランタイム ライブラリのソース ファイルを調べると場合、表示されます、既定の割り当てフック関数を**CrtDefaultAllocHook** (単に返す**TRUE**)、独自の個別のファイルにあります。DBGHOOK します。C. 割り当てフック関数、アプリケーションの前に実行されるランタイム スタートアップ コードで行われた割り当ての場合でも呼び出す場合**メイン**関数の代わりに、独自のいずれかでこの既定の関数を置き換えることができます使用して[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)します。  
  
## <a name="see-also"></a>関連項目  
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
