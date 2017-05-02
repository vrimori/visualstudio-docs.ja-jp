---
title: "IProcessDebugManager::RemoveApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.RemoveApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::RemoveApplication"
ms.assetid: 334e869d-81ae-4d30-9e89-89763ad4f184
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::RemoveApplication
実行中のアプリケーションの一覧からアプリケーションを削除します。  
  
## 構文  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### パラメーター  
 `dwAppCookie`  
 \[入力\]クッキーは `IProcessDebugManager::AddApplication` によってアプリケーションがアプリケーションの一覧に追加したときに提供します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、実行中のアプリケーションの一覧からアプリケーションを削除します。  
  
## 参照  
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)   
 [IProcessDebugManager インターフェイス](../../winscript/reference/iprocessdebugmanager-interface.md)