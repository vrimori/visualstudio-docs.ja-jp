---
title: "IDebugApplication::FireDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FireDebuggerEvent
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FireDebuggerEvent"
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FireDebuggerEvent
デバッガーの `IApplicationDebugger` のインターフェイスに汎用イベントを発生させます。  
  
## 構文  
  
```  
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### パラメーター  
 `riid`  
 \[入力\]オブジェクトの GUID。  
  
 `punk`  
 \[入力\]デバッガーに渡すイベント オブジェクト。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|メソッドは、現在実行されません。|  
  
## 解説  
 GUID のセマンティクスと `IUnknown` は完全に定義されたアプリケーションとデバッガーがあります。  
  
 このメソッドは、デバッガーのモデル カスタム拡張を可能にします; これは、現在実行されません。  
  
 このメソッドは `IApplicationDebugger::onDebuggerEvent` を呼び出します。  
  
## 参照  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)