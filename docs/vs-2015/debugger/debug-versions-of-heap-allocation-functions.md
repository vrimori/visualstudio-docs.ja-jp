---
title: ヒープ割り当て関数のデバッグ バージョン |Microsoft Docs
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
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7a649d8afd3ae7bf7d6d9abff98734ac96e05cd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802108"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>デバッグ バージョンのヒープ割り当て関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C ランタイム ライブラリには、デバッグ バージョンの特殊なヒープ割り当て関数があります。 これらの関数は、リリース バージョンの関数名の末尾に "_dbg" を追加した名前になっています。 ここでは、CRT 関数のリリース バージョンと _dbg バージョンとの相違点について、`malloc` と `_malloc_dbg` を例にして説明します。  
  
 ときに[_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a)が定義されている場合、CRT はすべて[malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0)呼び出し[_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)します。 したがって、`_malloc_dbg` の代わりに `malloc` を使用するようにコードを書き直さなくても、デバッグ中は利用できます。  
  
 しかし、明示的に `_malloc_dbg` を呼び出すこともできます。 明示的に `_malloc_dbg` を呼び出すと、さらに次の利点があります。  
  
- `_CLIENT_BLOCK` 型の割り当てを追跡できます。  
  
- 割り当て要求が発生したソース ファイルと行番号を格納できます。  
  
  変換したくない場合、`malloc`呼び出し`_malloc_dbg`、定義することで、ソース ファイル情報を取得できます[_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b)、プリプロセッサに直接マップを停止すると、すべての呼び出しを`malloc`に`_malloc_dbg`のラッパーではなく`malloc`します。  
  
  クライアント ブロック内の個々の割り当て型を追跡するには、`_malloc_dbg` パラメーターを `blockType` に設定して、直接 `_CLIENT_BLOCK` を呼び出す必要があります。  
  
  _DEBUG が定義されていないと呼び出しを`malloc`が影響を受けません、呼び出し`_malloc_dbg`に解決される`malloc`の定義[_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b)は無視され、ソース ファイルの情報に関連する、割り当て要求が指定されていません。 `malloc` にはブロック型を指定するパラメーターがないため、`_CLIENT_BLOCK` 型への割り当て要求は標準の割り当てとして扱われます。  
  
## <a name="see-also"></a>関連項目  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)



