---
title: "IActiveScriptSite::OnLeaveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnLeaveScript"
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnLeaveScript
スクリプト エンジンがスクリプト コードの実行が戻ったことをホストに通知します。  
  
## 構文  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## 戻り値  
 正常に終了した場合は `S_OK` を返します。  
  
## 解説  
 スクリプト エンジンは、スクリプト エンジンに入力した呼び出し元のアプリケーションに制御を返す前にこのメソッドを呼び出す必要があります。  たとえば、スクリプトがスクリプト エンジンによって処理されるイベントを発生させるオブジェクトを呼び出すと、スクリプト エンジンはイベントを実行する前に [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) のメソッドを呼び出してイベントを実装した後にイベントを発生させたオブジェクトへ `IActiveScriptSite::OnLeaveScript` 返される前にを呼び出す必要があります。  このメソッドの呼び出しは入れ子にできます。  `IActiveScriptSite::OnEnterScript` へのすべての呼び出しは、このメソッドに対応する呼び出しが必要です。  
  
## 参照  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)