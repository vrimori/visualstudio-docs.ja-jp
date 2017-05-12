---
title: "IActiveScriptSite::OnEnterScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnEnterScript"
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnEnterScript
スクリプト エンジンがスクリプト コードの実行が開始されたことをホストに通知します。  
  
## 構文  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## 戻り値  
 正常に終了した場合は `S_OK` を返します。  
  
## 解説  
 スクリプト エンジンは、スクリプト エンジンへの各エントリまたは再入でこのメソッドを呼び出す必要があります。  たとえば、スクリプトがスクリプト エンジンによって処理されるイベントを発生させるオブジェクトを呼び出すと、スクリプト エンジンはイベントを実行する前に `IActiveScriptSite::OnEnterScript` を呼び出して、イベントを実装した後にイベントを発生させたオブジェクトに戻す前に [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) のメソッドを呼び出す必要があります。  このメソッドの呼び出しは入れ子にできます。  このメソッドのすべての呼び出しに `IActiveScriptSite::OnLeaveScript`に対応する呼び出しが必要です。  
  
## 参照  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)