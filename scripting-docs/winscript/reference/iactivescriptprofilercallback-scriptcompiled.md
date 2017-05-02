---
title: "IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::ScriptCompiled
スクリプト エンジンがスクリプトをコンパイルするには、プロファイラー オブジェクトを通知します。  このメソッドは、コンパイルされるすべてのスクリプトに対して呼び出されます。  
  
## 構文  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### パラメーター  
 `scriptId`  
 \[入力\]コンパイルされたスクリプトの一意の ID。  この ID は、スクリプト エンジンによって割り当てられます。  
  
 `type`  
 \[入力\]コンパイルされたスクリプトの種類。  値は [PROFILER\_SCRIPT\_TYPE 列挙型](../../winscript/reference/profiler-script-type-enumeration.md)で定義されます。  
  
 `pIDebugDocumentContext`  
 \[入力\]使用できる場合は、プロファイラーが [IDebugDocumentContext インターフェイス](../../winscript/reference/idebugdocumentcontext-interface.md) のポインターについて照会する必要のある `IUnknown` インターフェイスへのポインター。  それ以外の場合、これは null です。  
  
## 戻り値  
 このメソッドの戻り値は、スクリプト エンジンでは無視されます。  
  
## 解説  
 スクリプト エンジンは、ホストによってサポートされている場合のみドキュメントのコンテキストを提供できます。  
  
## 参照  
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)