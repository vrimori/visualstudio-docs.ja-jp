---
title: "IRemoteDebugApplicationEvents::OnDisconnectDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnDisconnectDebugger
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnDisconnectDebugger"
ms.assetid: ea11cde0-1484-4181-a5dd-a1f6cf788892
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnDisconnectDebugger
デバッガーのドロップ イベントを処理します。  
  
## 構文  
  
```  
HRESULT OnDisconnectDebugger();  
```  
  
#### パラメーター  
 このメソッドは、パラメーターを受け取りません。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、デバッガーのドロップ イベントを処理します。  
  
## 参照  
 [IRemoteDebugApplicationEvents インターフェイス](../../winscript/reference/iremotedebugapplicationevents-interface.md)