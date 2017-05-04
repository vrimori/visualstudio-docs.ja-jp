---
title: "IActiveScriptProfilerCallback::Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback::Shutdown
プロファイリングを行う場合は、スクリプト エンジンで停止するたびに、プロファイラーのオブジェクトに通知するために呼び出されます。  この方法では、プロファイラー オブジェクト必要に応じてクリーンアップ ルーチンを呼び出すことができます。  このメソッドは、スクリプト エンジンによって、スクリプト エンジンがシャットダウンされるか、または [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) の呼び出しが失敗したときに呼び出されます。  
  
## 構文  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### パラメーター  
 `hrReason`  
 \[入力\]クロージャの理由。  スクリプト エンジンがシャットダウンするよう、`S_OK` が渡されます。  [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) の呼び出しがエラー HRESULT を返した場合、HRESULT が渡されます。  それ以外の場合、この値は [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)から取得されます。  
  
## 戻り値  
 このメソッドの戻り値は、スクリプト エンジンでは無視されます。  
  
## 参照  
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)