---
title: "IActiveScriptDebug インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptDebug インターフェイス"
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug インターフェイス
デバッグをサポートするスクリプト エンジンによって実装されます。  通常、の実装が `IActiveScriptDebug` インターフェイス `IActiveScript` インターフェイスを実装すること、オブジェクト。  その場合は、`IActiveScriptDebug` のインターフェイスを取得するに `IActiveScript::QueryInterface` のメソッドを呼び出します。  
  
 `IActiveScriptDebug` のインターフェイスは手段が用意されています:  
  
-   ドキュメントの管理を引き継ぐスマート ホスト。  
  
-   複数のスクリプト エンジンのデバッグを同期プロセス デバッグ マネージャー。  
  
 `IUnknown` から継承するメソッドに加え、`IActiveScriptDebug` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|スクリプトの任意のテキスト ブロックのテキスト属性を返します。|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|任意スクリプトレットのテキスト属性を返します。|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|`IDebugDocumentContext::EnumCodeContexts`へのデリゲート。|