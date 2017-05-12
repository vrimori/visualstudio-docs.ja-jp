---
title: "IActiveScriptProfilerCallback2::OnFunctionExitByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionExitByName"
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerCallback2::OnFunctionExitByName
そのプロファイラー オブジェクトを、スクリプト エンジンに既知ら Document Object Model \(DOM\) の関数呼び出しを実行します。  
  
## 構文  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### パラメーター  
 `pwszFunctionName`  
 \[出力\]この関数の名前は、スクリプト エンジン実行を終了します。  
  
 `scriptType`  
 \[入力\]関数の型。  有効な値については、[PROFILER\_SCRIPT\_TYPE 列挙型](../../winscript/reference/profiler-script-type-enumeration.md)を参照してください。  
  
## 戻り値  
 このメソッドの戻り値は、スクリプト エンジンでは無視されます。  
  
## 解説  
 DOM の呼び出しでは、スクリプト エンジンは [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)を呼び出す代わりに、このメソッドを呼び出します。  これにより、DOM 複数の一意なメソッドとプロパティがあります。  
  
## 参照  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2 インターフェイス](../../winscript/reference/iactivescriptprofilercallback2-interface.md)