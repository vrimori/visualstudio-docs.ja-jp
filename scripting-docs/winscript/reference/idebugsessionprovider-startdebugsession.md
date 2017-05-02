---
title: "IDebugSessionProvider::StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProvider.StartDebugSession
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugSessionProvider::StartDebugSession"
ms.assetid: 47697dfb-d4e1-492c-a14f-753e28195a76
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSessionProvider::StartDebugSession
指定したアプリケーションのデバッグ セッションを開始します。  
  
## 構文  
  
```  
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
);  
```  
  
#### パラメーター  
 `pda`  
 \[入力\]デバッグ アプリケーションを指定します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、指定されたアプリケーションのデバッグ セッションを開始します。  デバッガーはこの呼び出しから戻る前に `IRemoteDebugApplication::ConnectDebugger` を呼び出す必要があります。  
  
## 参照  
 [IDebugSessionProvider インターフェイス](../../winscript/reference/idebugsessionprovider-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)