---
title: "IActiveScriptProfilerCallback2 インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2 インターフェイス"
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback2 インターフェイス
Document Object Model \(DOM\) イベントが発生すると、プロファイラー オブジェクトに通知するためにスクリプト エンジンが使用するメソッドを提供します。  このインターフェイスは、プロファイラー オブジェクトによって実装されます。  
  
## メソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|スクリプト エンジンが DOM 関数呼び出しを移動先のオブジェクトのことをプロファイラーに通知します。|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|そのプロファイラー オブジェクトを、スクリプト エンジンに通知する DOM 関数呼び出しを実行します。|  
  
## 解説  
 最初にリリースされた Internet Explorer 9 がインストールされている `IActiveScriptProfilerCallback2` のインターフェイス。  
  
 DOM の呼び出しではない関数呼び出しの通知は [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)によって提供されます。  
  
> [!NOTE]
>  開始し、スクリプトの実行中にプロファイリングを停止機能を追加するには、次のメソッドを呼び出します。  これらのメソッドを使用して、またはプロファイリングを停止と [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] が実行中のすべての呼び出し履歴を取得できます。  
>   
>  -   プロファイリングを開始したことをプロファイラーに通知するために [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) を呼び出します。  
> -   このプロファイリングを停止ことをプロファイラーに通知するために [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) を呼び出します。  
  
## 参照  
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)