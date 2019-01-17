---
title: IActiveScriptProfilerControl インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7caa09f384ce460a3e73b21b10d6d8022182dde7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349492"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl インターフェイス
プロファイリングをサポートするスクリプト エンジンによって実装されます。 通常、実装するオブジェクト、`IActiveScriptProfilerControl`実装も、 [IActiveScript](../../winscript/reference/iactivescript.md)インターフェイス。 この場合を識別するハンドルを取得できます、`IActiveScriptProfilerControl`インターフェイスを呼び出すことによって、`IUnknown::QueryInterface`オブジェクトのメソッド。 インターフェイスは、停止とスクリプト エンジンのプロファイリングを開始するために必要なメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|スクリプト エンジンのプロファイリングを開始します。|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|スクリプト エンジンで、profiler イベント マスクを設定します。|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|スクリプト エンジンのプロファイリングを停止します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)