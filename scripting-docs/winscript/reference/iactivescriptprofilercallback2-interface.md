---
title: IActiveScriptProfilerCallback2 インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6109e028dfc51a88314ce597a67847e95f7eaaed
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349362"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 インターフェイス
ドキュメント オブジェクト モデル (DOM) のイベントが発生したときにプロファイラー オブジェクトを通知するスクリプト エンジンで使用されるメソッドを提供します。 このインターフェイスは、プロファイラー オブジェクトによって実装されます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|プロファイラーのオブジェクト、スクリプト エンジンが DOM の関数呼び出しを実行することを通知します。|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|DOM の関数呼び出しを実行して、スクリプト エンジン オブジェクトが完了したら、プロファイラーに通知します。|  
  
## <a name="remarks"></a>Remarks  
 `IActiveScriptProfilerCallback2` Internet Explorer 9 と共にリリースされた最初のインターフェイス。  
  
 DOM への呼び出しではない関数呼び出しの通知がによって提供される、 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)します。  
  
> [!NOTE]
>  プロファイリング、スクリプトが実行されているときに開始および停止する機能を追加するには、次のメソッドを呼び出します。 これらのメソッドを使用する場合、完全な呼び出し履歴を取得できます[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]開始またはプロファイリングを停止するときに実行します。  
> 
> - 呼び出す[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)をプロファイリングが開始したことをプロファイラーに通知します。  
>   -   呼び出す[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)をプロファイリングするをすぐに停止することをプロファイラーに通知します。  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)