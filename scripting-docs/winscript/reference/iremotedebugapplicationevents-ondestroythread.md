---
title: "IRemoteDebugApplicationEvents::OnDestroyThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnDestroyThread
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnDestroyThread"
ms.assetid: 7c716ccc-7b82-41b2-9a16-d0366999dee8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnDestroyThread
スレッド破棄されたイベントを処理します。  
  
## 構文  
  
```  
HRESULT OnDestroyThread(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### パラメーター  
 `prdat`  
 \[入力\]破棄されたスレッド。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、スレッド破棄されたイベントを処理します。  
  
## 参照  
 [IRemoteDebugApplicationEvents インターフェイス](../../winscript/reference/iremotedebugapplicationevents-interface.md)