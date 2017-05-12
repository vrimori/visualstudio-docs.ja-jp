---
title: "IActiveScriptSiteDebug::GetApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetApplication"
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetApplication
このスクリプトのサイトに関連付けられたデバッグ アプリケーション オブジェクトを返します。  
  
## 構文  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### パラメーター  
 `ppda`  
 \[入力\]スクリプトのサイトに関連付けられたデバッグ アプリケーション オブジェクトへのポインター。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|ホストはデバッグを直接サポートしていません。|  
  
## 解説  
 `GetApplication` のメソッドは、スマート ホストする方法を各スクリプトが属するアプリケーション オブジェクトを定義できます。  スクリプト エンジンは、これが失敗した場合に `IProcessDebugManager::GetDefaultApplication` 含むアプリケーションとリゾートを取得するときにこのメソッドを呼び出すようにする必要があります。  
  
## 参照  
 [IActiveScriptSiteDebug インターフェイス](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)