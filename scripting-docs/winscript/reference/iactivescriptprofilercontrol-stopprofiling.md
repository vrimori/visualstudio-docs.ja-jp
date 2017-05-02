---
title: "IActiveScriptProfilerControl::StopProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StopProfiling
apilocation: scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerControl::StopProfiling
スクリプト エンジンでプロファイリングを停止します。  このメソッドは、プロファイラー オブジェクトの [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) を呼び出し、それを解放します。  
  
## 構文  
  
```  
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### パラメーター  
 `hrShutdownReason`  
 \[入力\]プロファイラー オブジェクトの [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) のメソッドにパラメーターとして渡される HRESULT。  
  
## 戻り値  
 HRESULT を返します。  次の値を指定できます。  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|プロファイルは有効になりません。|  
  
## 参照  
 [IActiveScriptProfilerControl インターフェイス](../../winscript/reference/iactivescriptprofilercontrol-interface.md)