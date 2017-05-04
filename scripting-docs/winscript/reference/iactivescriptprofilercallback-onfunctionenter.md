---
title: "IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionEnter
スクリプト エンジンが Document Object Model \(DOM\) の呼び出しではない関数呼び出しを実行する直前であることを通知します。プロファイラー オブジェクト  
  
## 構文  
  
```  
HRESULT OnFunctionEnter(  
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
 DOM の呼び出しでは、スクリプト エンジンは `IActiveScriptProfilerCallback::OnFunctionEnter`の代わりに [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) を呼び出します。  これにより、DOM 複数の一意なメソッドとプロパティがあります。  
  
## 参照  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)