---
title: IActiveScriptProfilerControl インターフェイス |Microsoft ドキュメント
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
ms.openlocfilehash: f0d598302ae78ca0b2a1e7c1f94c949800378a2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724672"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl インターフェイス
プロファイリングをサポートするスクリプト エンジンによって実装されます。 通常を実装するオブジェクト、`IActiveScriptProfilerControl`も実装して、 [IActiveScript](../../winscript/reference/iactivescript.md)インターフェイスです。 この場合へのハンドルを取得できます、`IActiveScriptProfilerControl`インターフェイスを呼び出して、`IUnknown::QueryInterface`オブジェクトのメソッドです。 インターフェイスは、停止し、スクリプト エンジンでプロファイリングを開始するために必要なメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|スクリプト エンジンでプロファイリングを開始します。|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|スクリプト エンジンのプロファイラー イベント マスクを設定します。|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|スクリプト エンジンでプロファイリングを停止します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)