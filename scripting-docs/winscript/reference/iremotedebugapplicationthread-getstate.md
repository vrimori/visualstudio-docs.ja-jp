---
title: "IRemoteDebugApplicationThread::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetState"
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetState
このスレッドの状態を取得します。  
  
## 構文  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### パラメーター  
 `pState`  
 \[入力\]次のスレッド状態のフラグの組み合わせを設定します:  
  
|定数|値|説明|  
|--------|-------|--------|  
|THREAD\_STATE\_RUNNING|0x00000001|スレッドは実行されています。|  
|THREAD\_STATE\_SUSPENDED|0x00000002|スレッドが中断される。|  
|THREAD\_BLOCKED|0x00000004|スレッドがブロックされています。|  
|THREAD\_OUT\_OF\_CONTEXT|0x00000008|スレッドがコンテンツからです。|  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、このスレッドの状態を取得します。  
  
## 参照  
 [IRemoteDebugApplicationThread インターフェイス](../../winscript/reference/iremotedebugapplicationthread-interface.md)