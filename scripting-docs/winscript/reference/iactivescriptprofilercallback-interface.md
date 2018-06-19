---
title: IActiveScriptProfilerCallback インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc4b9d4e3b1f83a37e64e3a85387fd378d3ca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724582"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback インターフェイス
イベントが発生したときに、プロファイラーのオブジェクトを通知するスクリプト エンジンが使用されるメソッドを提供します。 このインターフェイスは、プロファイラーのオブジェクトによって実装されます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|スクリプト エンジンでプロファイリングが開始されるたびに、プロファイラーのオブジェクトを初期化するために呼び出されます。|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|解放し、プロファイラーのオブジェクトを解放スクリプト エンジンでプロファイリングを停止するたびに呼び出されます。|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|エンジンのスクリプティング オブジェクト、スクリプトのコンパイルをプロファイラーに通知します。|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|エンジン スクリプティング オブジェクト、スクリプトをコンパイルするときに、関数が発生しました、プロファイラーに通知します。|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|ドキュメント オブジェクト モデル (DOM) への呼び出しではない関数呼び出しの実行をスクリプト エンジンでは、プロファイラーのオブジェクトに通知します。|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|オブジェクト、スクリプト エンジンで関数の実行が完了を呼び出すことがないこと DOM への呼び出しをプロファイラーに通知します。|  
  
## <a name="remarks"></a>コメント  
 関数呼び出しにドキュメント オブジェクト モデル (DOM) の通知がによって提供される、 [IActiveScriptProfilerCallback2 インターフェイス](../../winscript/reference/iactivescriptprofilercallback2-interface.md)です。  
  
> [!NOTE]
>  起動し、スクリプトの実行中のプロファイリングを停止する機能を追加するには、次のメソッドを呼び出します。 これらのメソッドを使用する場合、完全な呼び出し履歴を取得できます[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]開始またはプロファイリングを停止するときに実行します。  
>   
>  -   呼び出す[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)をプロファイリングを開始していることをプロファイラーに通知します。  
> -   呼び出す[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)をプロファイリングを停止することだけ早くはプロファイラーに通知します。  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)