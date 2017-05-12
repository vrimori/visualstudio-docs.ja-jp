---
title: "IActiveScriptSite::OnStateChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnStateChange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnStateChange"
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSite::OnStateChange
スクリプト エンジンの状態を変更したことをホストに通知します。  
  
## 構文  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### パラメーター  
 `ssScriptState`  
 \[入力\]評価します。新しいスクリプトの状態を示す。  状態の詳細については、[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) のメソッドを参照してください。  
  
## 戻り値  
 正常に終了した場合は `S_OK` を返します。  
  
## 参照  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)