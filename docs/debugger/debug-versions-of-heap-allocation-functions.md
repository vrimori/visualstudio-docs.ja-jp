---
title: "デバッグ バージョンのヒープ割り当て関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.crt"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CRTDBG_MAP_ALLOC マクロ"
  - "_malloc_dbg 関数"
  - "デバッグ [CRT], ヒープ割り当て関数"
  - "デバッグ (メモリ リークの), CRT デバッグ ライブラリ関数"
  - "ヒープ割り当て, デバッグ"
  - "malloc 関数"
  - "メモリ リーク, CRT デバッグ ライブラリ関数"
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# デバッグ バージョンのヒープ割り当て関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

C ランタイム ライブラリには、デバッグ バージョンの特殊なヒープ割り当て関数があります。  これらの関数は、リリース バージョンの関数名の末尾に "\_dbg" を追加した名前になっています。  ここでは、CRT 関数のリリース バージョンと \_dbg バージョンとの相違点について、`malloc` と `_malloc_dbg` を例にして説明します。  
  
 [\_DEBUG](/visual-cpp/c-runtime-library/debug) が定義されている場合、CRT はすべての [malloc](/visual-cpp/c-runtime-library/reference/malloc) 呼び出しを [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg) に置き換えます。  したがって、`malloc` の代わりに `_malloc_dbg` を使用するようにコードを書き直さなくても、デバッグ中は利用できます。  
  
 しかし、明示的に `_malloc_dbg` を呼び出すこともできます。  明示的に `_malloc_dbg` を呼び出すと、さらに次の利点があります。  
  
-   `_CLIENT_BLOCK` 型の割り当てを追跡できます。  
  
-   割り当て要求が発生したソース ファイルと行番号を格納できます。  
  
 `malloc` 呼び出しを `_malloc_dbg` 呼び出しに変換せずに、ソース ファイル情報を取得するには、[\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) を定義します。これにより、`malloc` のラッパーを利用するのではなく、プリプロセッサがすべての `malloc` 呼び出しを直接 `_malloc_dbg` に置き換えます。  
  
 クライアント ブロック内の個々の割り当て型を追跡するには、`blockType` パラメーターを `_CLIENT_BLOCK` に設定して、直接 `_malloc_dbg` を呼び出す必要があります。  
  
 \_DEBUG が定義されていない場合は、`malloc` 呼び出しはそのままですが、`_malloc_dbg` 呼び出しは `malloc` に変換されます。また、[\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) が定義されていても無視されるため、割り当て要求に関連するソース ファイル情報を取得することはできません。  `malloc` にはブロック型を指定するパラメーターがないため、`_CLIENT_BLOCK` 型への割り当て要求は標準の割り当てとして扱われます。  
  
## 参照  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)