---
title: "IActiveScriptProfilerCallback インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IActiveScriptProfilerCallback インターフェイス
イベントが発生すると、プロファイラー オブジェクトに通知するためにスクリプト エンジンが使用するメソッドを提供します。  このインターフェイスは、プロファイラー オブジェクトによって実装されます。  
  
## メソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|プロファイリングを行ってスクリプト エンジンから起動されるたびに、プロファイラー オブジェクトを初期化するために呼び出されます。|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|プロファイリングを行う場合は、スクリプト エンジンで停止するたびに、プロファイラー オブジェクトを解放し、解放するために呼び出されます。|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|スクリプト エンジンがスクリプトをコンパイルするには、プロファイラー オブジェクトを通知します。|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|スクリプトをコンパイルすると、スクリプト エンジンの関数にヒットしたことを通知します。プロファイラー オブジェクト|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|スクリプト エンジンが Document Object Model \(DOM\) の呼び出しではない関数呼び出しを実行する直前であることを通知します。プロファイラー オブジェクト|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|そのプロファイラー オブジェクトを、スクリプト エンジンに通知する DOM の呼び出しではない関数呼び出しを実装します。|  
  
## 解説  
 \(DOM\) ドキュメント オブジェクト モデルへの関数呼び出しの通知は [IActiveScriptProfilerCallback2 インターフェイス](../../winscript/reference/iactivescriptprofilercallback2-interface.md)によって提供されます。  
  
> [!NOTE]
>  開始し、スクリプトの実行中にプロファイリングを停止機能を追加するには、次のメソッドを呼び出します。  これらのメソッドを使用して、またはプロファイリングを停止と [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] が実行中のすべての呼び出し履歴を取得できます。  
>   
>  -   プロファイリングを開始したことをプロファイラーに通知するために [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) を呼び出します。  
> -   このプロファイリングを停止ことをプロファイラーに通知するために [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) を呼び出します。  
  
## 参照  
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)