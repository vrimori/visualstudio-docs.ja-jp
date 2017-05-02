---
title: "IRemoteDebugApplicationThread::GetApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetApplication"
ms.assetid: 9446c7f9-cfa2-408f-98c5-64f549783de1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetApplication
このスレッドに関連付けられたアプリケーション オブジェクトを返します。  
  
## 構文  
  
```  
HRESULT GetApplication(  
   IRemoteDebugApplication**  pprda  
);  
```  
  
#### パラメーター  
 `pprda`  
 \[出力\]このスレッドに関連付けられたアプリケーション オブジェクト。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、このスレッドに関連付けられたアプリケーション オブジェクトを返します。  
  
## 参照  
 [IRemoteDebugApplicationThread インターフェイス](../../winscript/reference/iremotedebugapplicationthread-interface.md)