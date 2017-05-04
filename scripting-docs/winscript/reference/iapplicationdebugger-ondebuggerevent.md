---
title: "IApplicationDebugger::onDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onDebuggerEvent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onDebuggerEvent"
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onDebuggerEvent
カスタム アプリケーションのイベントを処理します。  
  
## 構文  
  
```  
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### パラメーター  
 `riid`  
 \[入力\]オブジェクトのインターフェイス ID。  
  
 `punk`  
 \[入力\]インターフェイスを実装するイベント オブジェクト、`riid`で定義されています。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|メソッドは、現在実行されません。|  
  
## 解説  
 `IUnknown` のセマンティクスは完全に定義されたアプリケーションとデバッガーがあります。  
  
 このメソッドは、デバッガーのモデル カスタム拡張を可能にします; これは、現在実行されません。  
  
 このメソッドは `IDebugApplication::FireDebuggerEvent` が呼び出されたときに呼び出されます。  
  
## 参照  
 [IApplicationDebugger インターフェイス](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)