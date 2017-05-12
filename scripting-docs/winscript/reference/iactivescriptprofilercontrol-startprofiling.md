---
title: "IActiveScriptProfilerControl::StartProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerControl::StartProfiling
スクリプト エンジンでプロファイリングを開始します。  スクリプト エンジンは呼び出すことで [CoCreateInstance](http://msdn.microsoft.com/ja-jp/7295a55b-12c7-4ed0-a7a4-9ecee16afdec)へのプロファイラー オブジェクトのインスタンスを作成します。  
  
## 構文  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### パラメーター  
 `clsidProfilerObject`  
 \[入力\]作成するプロファイラー オブジェクトのクラス ID \(CLSID\)。  
  
 `dwEventMask`  
 \[入力\]イベントの種類を指定する 4 バイトのビットマスク。  ビットが [PROFILER\_EVENT\_MASK 列挙型](../../winscript/reference/profiler-event-mask-enumeration.md)で定義されます。  
  
 `dwContext`  
 \[入力\]プロファイラー オブジェクトに渡される A の 4 バイト値。  
  
## 戻り値  
 HRESULT を返します。  次の値を指定できます。  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`ACTIVPROF_E_PROFILER_PRESENT`|プロファイルは既に有効になっています。|  
  
## 参照  
 [IActiveScriptProfilerControl インターフェイス](../../winscript/reference/iactivescriptprofilercontrol-interface.md)