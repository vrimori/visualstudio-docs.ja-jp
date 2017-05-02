---
title: "IActiveScriptProfilerControl::SetProfilerEventMask | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.SetProfilerEventMask
apilocation: scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptProfilerControl::SetProfilerEventMask
スクリプト エンジンが発生させるイベントの種類を指定する 4 バイトのビットマスクを設定します。  
  
## 構文  
  
```  
RESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### パラメーター  
 `dwEventMask`  
 \[入力\]イベントの種類を指定する 4 バイトのビットマスク。  ビットが [PROFILER\_EVENT\_MASK 列挙型](../../winscript/reference/profiler-event-mask-enumeration.md)で定義されます。  
  
## 戻り値  
 HRESULT を返します。  次の値を指定できます。  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|プロファイルは有効になりません。|  
  
## 参照  
 [IActiveScriptProfilerControl インターフェイス](../../winscript/reference/iactivescriptprofilercontrol-interface.md)