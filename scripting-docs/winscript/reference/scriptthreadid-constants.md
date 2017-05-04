---
title: "SCRIPTTHREADID 定数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADID"
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# SCRIPTTHREADID 定数
スレッドの種類を指定するために使用します。  
  
## 構文  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## 定数  
  
|定数|値|説明|  
|--------|-------|--------|  
|SCRIPTTHREADID\_CURRENT|0xFFFFFFFD|現在実行中のスレッド。|  
|SCRIPTTHREADID\_BASE|0xFFFFFFFE|基本スレッド; つまり、スクリプト エンジンのインスタンスが作成されたスレッド。|  
|SCRIPTTHREADID\_ALL|0xFFFFFFFF|すべてのスレッド。|  
  
## 解説  
 `SCRIPTTHREADID` の型は `IActiveScript::GetCurrentScriptThreadID`、`IActiveScript::GetScriptThreadID`、`IActiveScript::GetScriptThreadState`と `IActiveScript::InterruptScriptThread`によって使用されます `IActiveScript::GetScriptThreadState` は、定数と `IActiveScript::InterruptScriptThread`でのみ使用できます。  
  
## 参照  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)