---
title: "IActiveScriptProfilerCallback::OnFunctionExit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionExit
そのプロファイラー オブジェクトを、スクリプト エンジンに既知ら Document Object Model \(DOM\) の呼び出しではない関数呼び出しを実装します。  
  
## 構文  
  
```  
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### パラメーター  
 `scriptId`  
 \[入力\]関数を含んでいるスクリプトの一意の ID。  この ID は、スクリプト エンジンによって割り当てられます。  
  
 `functionId`  
 \[入力\]関数の一意の ID。  この ID は、スクリプト エンジンによって割り当てられます。  
  
## 戻り値  
 このメソッドの戻り値は、スクリプト エンジンでは無視されます。  
  
## 解説  
 DOM の呼び出しでは、スクリプト エンジンは `IActiveScriptProfilerCallback::OnFunctionExit`の代わりに [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) を呼び出します。  これにより、DOM 複数の一意なメソッドとプロパティがあります。  
  
## 参照  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)