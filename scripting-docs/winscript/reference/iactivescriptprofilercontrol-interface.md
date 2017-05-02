---
title: "IActiveScriptProfilerControl インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerControl インターフェイス
サポートのプロファイルは、スクリプト エンジンによって実装されます。  通常、実装が `IActiveScriptProfilerControl`[IActiveScript](../../winscript/reference/iactivescript.md) インターフェイスを実装すること、オブジェクト。  この場合、`IActiveScriptProfilerControl` のインターフェイスにオブジェクトの `IUnknown::QueryInterface` のメソッドを呼び出して、ハンドルを取得できます。  インターフェイスは、スクリプト エンジンでプロファイリングを停止したり起動するために必要なメソッドを提供します。  
  
## メソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|スクリプト エンジンでプロファイリングを開始します。|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|スクリプト エンジンのプロファイラー イベントのマスクを設定します。|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|スクリプト エンジンでプロファイリングを停止します。|  
  
## 参照  
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)