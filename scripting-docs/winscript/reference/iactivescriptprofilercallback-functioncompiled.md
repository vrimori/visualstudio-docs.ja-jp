---
title: "IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::FunctionCompiled
スクリプトをコンパイルすると、スクリプト エンジンの関数にヒットしたことを通知します。プロファイラー オブジェクト  
  
## 構文  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### パラメーター  
 `functionId`  
 \[入力\]関数の一意の ID。  この ID は、スクリプト エンジンによって割り当てられます。  
  
 `scriptId`  
 \[入力\]関数を含んでいるスクリプトの一意の ID。  
  
 `pwszFunctionName`  
 \[入力\]匿名関数の関数、または null の名前。  
  
 `pwszFunctionNameHint`  
 \[入力\]スクリプト エンジンが名前を推測する関数、または null の、推論された名前。  
  
 `pIDebugDocumentContext`  
 \[入力\]使用できる場合は、プロファイラーが [IDebugDocumentContext インターフェイス](../../winscript/reference/idebugdocumentcontext-interface.md) のポインターについて照会する必要のある `IUnknown` インターフェイスへのポインター。  それ以外の場合は null。  
  
## 戻り値  
 このメソッドの戻り値は、スクリプト エンジンでは無視されます。  
  
## 解説  
 スクリプト エンジンは、ホストによってサポートされている場合のみドキュメントのコンテキストを提供できます。  
  
## 参照  
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)