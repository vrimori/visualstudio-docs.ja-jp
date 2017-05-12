---
title: "IActiveScriptErrorDebug インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug インターフェイス"
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug インターフェイス
コンパイル時のエラーおよび実行時にドキュメントの例外コンテキスト情報を提供します。  `IActiveScriptError::QueryInterface` のメソッドは `IActiveScriptErrorDebug` のインターフェイスをサポートします。  
  
 `IActiveScriptError` から継承するメソッドに加え、`IActiveScriptErrorDebug` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|このエラーがドキュメントのコンテキストを提供します。|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|ランタイム エラーについて有効なスタック フレームを提供します。|