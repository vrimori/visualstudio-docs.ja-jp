---
title: "IDiaLoadCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaLoadCallback2 インターフェイス"
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロシージャを検索する DIA のシンボルのコールバックを受信して検索処理に制限が適用されるようにします。  
  
## 構文  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## Vtable の順序でメソッド  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドも公開します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|元の Debug ディレクトリの .pdb ファイルを検索するかどうかを判定します。|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../Topic/IDiaLoadCallback2::RestrictReferencePathAccess.md)|.pdb ファイルを検索することにより.exe ファイルが存在するパスで許可されているかどうかを判定します。|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|デバッグ情報を検索するかどうかを.dbg ファイルから決定します。|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|.pdb ファイルの検索がシステムのルート ディレクトリに対して許可するかどうかを指定します。|  
  
## 解説  
 クライアント アプリケーションはこのインターフェイスを実装し[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) メソッドの呼び出しのアセンブリへの参照を提供します。  [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) すべてのインターフェイスのメソッドを実装することに注意してください。  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia80.dll  
  
## 参照  
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)