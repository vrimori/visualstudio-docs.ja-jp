---
title: "IMachineDebugManager::AddApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManager.AddApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManager::AddApplication"
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManager::AddApplication
実行中のアプリケーションのリストにアプリケーションが追加されます。  
  
## 構文  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### パラメーター  
 `pda`  
 \[入力\]実行中のアプリケーションのリストにアプリケーション。  
  
 `pdwAppCookie`  
 \[出力\]コンピューターのデバッグ マネージャーからアプリケーションを削除する A のクッキー。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、プロセス デバッグ マネージャーによって `IProcessDebugManager::AddApplication` が呼び出されるたびに呼び出されます。  
  
## 参照  
 [IMachineDebugManager インターフェイス](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)