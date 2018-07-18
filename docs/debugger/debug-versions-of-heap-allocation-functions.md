---
title: ヒープ割り当て関数のデバッグ バージョン |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e426da9491c13e0d6f9377814673ca41512e5e09
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470944"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>デバッグ バージョンのヒープ割り当て関数
C ランタイム ライブラリには、デバッグ バージョンの特殊なヒープ割り当て関数があります。 これらの関数は、リリース バージョンの関数名の末尾に "_dbg" を追加した名前になっています。 ここでは、CRT 関数のリリース バージョンと _dbg バージョンとの相違点について、`malloc` と `_malloc_dbg` を例にして説明します。  
  
 ときに[_DEBUG](/cpp/c-runtime-library/debug)が定義されている場合、CRT すべてマップ[malloc](/cpp/c-runtime-library/reference/malloc)呼び出し[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)です。 したがって、`_malloc_dbg` の代わりに `malloc` を使用するようにコードを書き直さなくても、デバッグ中は利用できます。  
  
 しかし、明示的に `_malloc_dbg` を呼び出すこともできます。 明示的に `_malloc_dbg` を呼び出すと、さらに次の利点があります。  
  
-   `_CLIENT_BLOCK` 型の割り当てを追跡できます。  
  
-   割り当て要求が発生したソース ファイルと行番号を格納できます。  
  
 変換したくない場合、`malloc`呼び出し`_malloc_dbg`、定義することで、ソース ファイル情報を取得することができます[_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)、プリプロセッサに直接マップを停止すると、すべての呼び出しを`malloc`に`_malloc_dbg`をラップするラッパーではなく`malloc`です。  
  
 クライアント ブロック内の個々の割り当て型を追跡するには、`_malloc_dbg` パラメーターを `blockType` に設定して、直接 `_CLIENT_BLOCK` を呼び出す必要があります。  
  
 _DEBUG が定義されていないと呼び出しを`malloc`に影響しませんが、呼び出し`_malloc_dbg`に解決される`malloc`の定義[_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)は無視され、ソース ファイルの情報に関連する、割り当て要求が指定されていません。 `malloc` にはブロック型を指定するパラメーターがないため、`_CLIENT_BLOCK` 型への割り当て要求は標準の割り当てとして扱われます。  
  
## <a name="see-also"></a>関連項目  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)