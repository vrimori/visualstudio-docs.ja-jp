---
title: "IDebugHelper インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugHelper インターフェイス"
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper インターフェイス
オブジェクト ブラウザー、および単純な接続ポイントのファクトリとして機能します。  \(PDM\) プロセス デバッグ マネージャーは、スクリプト エンジンによって実装されるこのインターフェイスを実装します。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugHelper` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|バリアントをラップするプロパティ ブラウザーを返します。|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|バリアントをラップする戻り、文字列への変数の値または VARTYPE の型のカスタム変換を使用してプロパティ ブラウザーが。|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|`IDispatch` の特定のオブジェクトをラップするイベント インターフェイスを返します。|