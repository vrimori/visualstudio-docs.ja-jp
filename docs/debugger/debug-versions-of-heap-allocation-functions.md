---
title: ヒープ割り当て関数のデバッグ バージョン |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf3865d8369b7b3b4a7407f8c54465f93bcc7bd7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920885"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>デバッグ バージョンのヒープ割り当て関数
C ランタイム ライブラリには、デバッグ バージョンの特殊なヒープ割り当て関数があります。 これらの関数は、リリース バージョンの関数名の末尾に "_dbg" を追加した名前になっています。 ここでは、CRT 関数のリリース バージョンと _dbg バージョンとの相違点について、`malloc` と `_malloc_dbg` を例にして説明します。  
  
 ときに[_DEBUG](/cpp/c-runtime-library/debug)が定義されている場合、CRT はすべて[malloc](/cpp/c-runtime-library/reference/malloc)呼び出し[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)します。 したがって、`_malloc_dbg` の代わりに `malloc` を使用するようにコードを書き直さなくても、デバッグ中は利用できます。  
  
 しかし、明示的に `_malloc_dbg` を呼び出すこともできます。 明示的に `_malloc_dbg` を呼び出すと、さらに次の利点があります。  
  
- `_CLIENT_BLOCK` 型の割り当てを追跡できます。  
  
- 割り当て要求が発生したソース ファイルと行番号を格納できます。  
  
  変換したくない場合、`malloc`呼び出し`_malloc_dbg`、定義することで、ソース ファイル情報を取得できます[_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)、プリプロセッサに直接マップを停止すると、すべての呼び出しを`malloc`に`_malloc_dbg`のラッパーではなく`malloc`します。  
  
  クライアント ブロック内の個々の割り当て型を追跡するには、`_malloc_dbg` パラメーターを `blockType` に設定して、直接 `_CLIENT_BLOCK` を呼び出す必要があります。  
  
  _DEBUG が定義されていないと呼び出しを`malloc`が影響を受けません、呼び出し`_malloc_dbg`に解決される`malloc`の定義[_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)は無視され、ソース ファイルの情報に関連する、割り当て要求が指定されていません。 `malloc` にはブロック型を指定するパラメーターがないため、`_CLIENT_BLOCK` 型への割り当て要求は標準の割り当てとして扱われます。  
  
## <a name="see-also"></a>関連項目
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)
