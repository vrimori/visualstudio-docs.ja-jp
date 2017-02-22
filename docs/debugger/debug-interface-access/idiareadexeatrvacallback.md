---
title: "IDiaReadExeAtRVACallback | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback インターフェイス"
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

相対仮想アドレスで指定された実行可能ファイルのバイト列を指定するクライアント アプリケーションを作成できます。  
  
## 構文  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## Vtable の順序でメソッド  
 次の表は `IDiaReadExeAtRVACallback` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|実行可能ファイルから指定した相対仮想アドレスから始まる指定 \(RVA\) したバイト数を読み取ります。|  
  
## 解説  
 クライアント アプリケーションは実行可能ファイルへの相対仮想アドレスを使う実行形式のバイトを作成するにはこのインターフェイスを実装します。  絶対ファイルのオフセットを使用するには[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)インターフェイスを実装します。  
  
## 呼び出し元のメモ  
 このメソッドはクライアント アプリケーションによって実装され[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) にファイルを読み取るための代替メソッドとしてメソッドに渡されます。  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia80.dll  
  
## 参照  
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)