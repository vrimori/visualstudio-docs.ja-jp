---
title: "IRemoteDebugApplicationEvents::OnCreateThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnCreateThread
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnCreateThread"
ms.assetid: 0b7c5181-eda6-4303-b4ae-d45962e8a3d3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnCreateThread
作成したスレッドのイベントを処理します。  
  
## 構文  
  
```  
HRESULT OnCreateThread(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### パラメーター  
 `prdat`  
 \[出力\]新しく作成されたスレッド。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、作成のスレッドのイベントを処理します。  
  
## 参照  
 [IRemoteDebugApplicationEvents インターフェイス](../../winscript/reference/iremotedebugapplicationevents-interface.md)