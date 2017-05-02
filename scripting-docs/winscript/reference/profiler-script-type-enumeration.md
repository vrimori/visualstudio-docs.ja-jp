---
title: "PROFILER_SCRIPT_TYPE 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_SCRIPT_TYPE
apilocation: scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# PROFILER_SCRIPT_TYPE 列挙型
スクリプトの種類を指定します。  
  
## 構文  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## メンバー  
  
|メンバー|説明|  
|----------|--------|  
|PROFILER\_SCRIPT\_TYPE\_USER|ユーザー作成スクリプト コードを指定します。|  
|PROFILER\_SCRIPT\_TYPE\_DYNAMIC|実行時に動的に生成されるスクリプト コードを指定します。|  
|PROFILER\_SCRIPT\_TYPE\_NATIVE|スクリプト エンジンで定義されたオブジェクトとネイティブ関数に対してスクリプトの種類を指定します。|  
|PROFILER\_SCRIPT\_TYPE\_DOM|`document.getElementById` のメソッドに Internet Explorer の Document Object Model \(DOM\)、たとえば、呼び出しの呼び出しを指定します。|  
  
## 参照  
 [アクティブ スクリプト プロファイラーの定数、列挙型、および構造体](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)