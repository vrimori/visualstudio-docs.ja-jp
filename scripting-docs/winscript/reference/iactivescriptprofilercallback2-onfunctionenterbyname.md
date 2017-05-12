---
title: "IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionEnterByName"
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerCallback2::OnFunctionEnterByName
スクリプト エンジンが Document Object Model \(DOM\) の関数呼び出しを実行しようとしているプロファイラー オブジェクトを通知します。  
  
## 構文  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### パラメーター  
 `pwszFunctionName`  
 \[入力\]実行するスクリプト エンジンがとしている関数の名前。  
  
 `scriptType`  
 \[入力\]関数の型。  有効な値については、[PROFILER\_SCRIPT\_TYPE 列挙型](../../winscript/reference/profiler-script-type-enumeration.md)を参照してください。  
  
## 戻り値  
 このメソッドの戻り値は、スクリプト エンジンでは無視されます。  
  
## 解説  
 DOM の呼び出しでは、スクリプト エンジンは [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)を呼び出す代わりに、このメソッドを呼び出します。  これにより、DOM 複数の一意なメソッドとプロパティがあります。  
  
## 参照  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2 インターフェイス](../../winscript/reference/iactivescriptprofilercallback2-interface.md)