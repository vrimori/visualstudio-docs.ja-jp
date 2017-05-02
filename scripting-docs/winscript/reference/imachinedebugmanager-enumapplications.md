---
title: "IMachineDebugManager::EnumApplications | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManager.EnumApplications
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManager::EnumApplications"
ms.assetid: 5d833db4-fd9b-4e61-bebb-130faede5a77
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManager::EnumApplications
実行中のアプリケーションの現在のリストの列挙子を返します。  
  
## 構文  
  
```  
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### パラメーター  
 `ppeda`  
 \[入力\]実行中のアプリケーションの現在の一覧を含む列挙子。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、実行中のアプリケーションの現在のリストの列挙子を返します。  デバッガーの IDE はアプリケーションをデバッグするために表示し、アタッチするには、このメソッドを使用します。  
  
## 参照  
 [IMachineDebugManager インターフェイス](../../winscript/reference/imachinedebugmanager-interface.md)