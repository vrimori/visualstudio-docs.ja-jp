---
title: 割り当てフック関数と C ランタイムのメモリの割り当て |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f7f81abd82857b3d9ed2161a6923a79b614bf5a
ms.sourcegitcommit: 0342f99120fbd603b8f06f7e9166c39f2896827a
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742402"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>割り当てフック関数と C ランタイムのメモリ割り当て
割り当てフック関数の非常に重要な制限は、無視する必要があります明示的に`_CRT_BLOCK`ブロックします。 これらのブロックは、内部のメモリを割り当てる C ランタイム ライブラリ関数を呼び出す場合、C ランタイム ライブラリ関数によって内部的に行われたメモリ割り当てです。 無視してかまいません`_CRT_BLOCK`割り当ての先頭に次のコードを含めることによってブロックが関数をフックします。

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

割り当てフック関数を無視しない場合`_CRT_BLOCK`フックで呼び出される C ランタイム ライブラリ関数が無限ループにプログラムをトラップし、ブロックします。 たとえば、`printf` は内部的にメモリを割り当てます。 フック コードで `printf` を呼び出すと、その結果行われる割り当てによって再びフックが呼び出され、それによって、スタック オーバーフローが発生するまで、再び **printf** が呼び出されるという繰り返しが発生します。 `_CRT_BLOCK` 型の割り当て処理をレポートする必要がある場合は、この制限事項を回避するために、C ランタイム関数ではなく Windows API 関数を使用して書式設定や出力を行う方法があります。 Windows Api では、C ランタイム ライブラリのヒープを使用しないために、無限ループで、割り当てフックをトラップされません。

ランタイム ライブラリのソース ファイルを調べる場合、既定の割り当て用のフック関数 **CrtDefaultAllocHook** (これは単に **TRUE** を返します) が独自の個別のファイル (DBGHOOK.C) の中にあることがわかります。 アプリケーションの **main** 関数の前に実行されるランタイムのスタートアップ コードによる割り当て時にも割り当てのフックが呼び出されるようにするには、[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) を使用する代わりに、この既定の関数を独自の関数に置き換えることができます。

## <a name="see-also"></a>関連項目
[デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)
