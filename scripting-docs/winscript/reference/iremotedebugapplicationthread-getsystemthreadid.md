---
title: "IRemoteDebugApplicationThread::GetSystemThreadId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetSystemThreadId
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetSystemThreadId"
ms.assetid: 6a6d5f62-4f60-4e87-9206-3c6f2e026d11
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetSystemThreadId
スレッドに関連付けられた動作システム参照先の識別子を返します。  
  
## 構文  
  
```  
HRESULT GetSystemThreadId(  
   DWORD*  dwThreadId  
);  
```  
  
#### パラメーター  
 `dwThreadId`  
 \[入力\]スレッドに関連付けられたシステム動作に依存する識別子。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 `dwThreadId` の値は、マシン全体で一意である必要はありません。  
  
## 参照  
 [IRemoteDebugApplicationThread インターフェイス](../../winscript/reference/iremotedebugapplicationthread-interface.md)