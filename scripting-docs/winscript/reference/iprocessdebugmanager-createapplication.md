---
title: "IProcessDebugManager::CreateApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.CreateApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::CreateApplication"
ms.assetid: d6b646f2-8af0-445c-ae7e-a9772042b3a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::CreateApplication
このアプリケーションの新しいデバッグ アプリケーション オブジェクトを作成します。  
  
## 構文  
  
```  
HRESULT CreateApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### パラメーター  
 `ppda`  
 \[出力\]このアプリケーションのデバッグ アプリケーション オブジェクト。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドで作成されるオブジェクトに名前がなく、実行中のアプリケーションのリストに追加されません。  アプリケーションの一覧にデバッグ アプリケーションを追加するに `IProcessDebugManager::AddApplication` を使用します。  
  
## 参照  
 [IProcessDebugManager インターフェイス](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)