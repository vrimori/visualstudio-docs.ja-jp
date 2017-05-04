---
title: "IActiveScriptProfilerCallback::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Initialize
apilocation: scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerCallback::Initialize
プロファイリングを行ってスクリプト エンジンから起動されるたびに、プロファイラー オブジェクトを初期化するために呼び出されます。  
  
## 構文  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### パラメーター  
 `dwContext`  
 \[入力\] [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)に渡される A の 4 バイト値。  
  
## 戻り値  
 HRESULT を返します。  次の値を指定できます。  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 メソッドでプロファイラーのオブジェクトを初期化できなかった場合、スクリプト エンジンに通知するエラー HRESULT を返す必要があります。  この場合、スクリプト エンジンは直接パラメーターの HRESULT を渡す [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)を呼び出さないでください。次に、プロファイラー オブジェクトを解放します。  
  
## 参照  
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)