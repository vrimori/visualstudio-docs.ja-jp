---
title: "IActiveScriptProfilerCallback2 インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dc9fcd8ca4afec0fb474c0f3a7317b608c7c9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 インターフェイス
ドキュメント オブジェクト モデル (DOM) のイベントが発生したときに、プロファイラーのオブジェクトを通知するスクリプト エンジンが使用されるメソッドを提供します。 このインターフェイスは、プロファイラーのオブジェクトによって実装されます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|スクリプト エンジンが、DOM 関数呼び出しを実行する予定のプロファイラーのオブジェクトに通知します。|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|エンジンのスクリプト オブジェクトでは、DOM 関数呼び出しの実行が完了をプロファイラーに通知します。|  
  
## <a name="remarks"></a>コメント  
 `IActiveScriptProfilerCallback2`インターフェイス最初 Internet Explorer 9 と共にリリースされました。  
  
 DOM への呼び出しではない関数呼び出しの通知がによって提供される、 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)です。  
  
> [!NOTE]
>  起動し、スクリプトの実行中のプロファイリングを停止する機能を追加するには、次のメソッドを呼び出します。 これらのメソッドを使用する場合、完全な呼び出し履歴を取得できます[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]開始またはプロファイリングを停止するときに実行します。  
>   
>  -   呼び出す[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)をプロファイリングを開始していることをプロファイラーに通知します。  
> -   呼び出す[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)をプロファイリングを停止することだけ早くはプロファイラーに通知します。  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)