---
title: "IActiveScriptSiteDebugEx インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx インターフェイス"
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebugEx インターフェイス
アプリケーションの実行時エラー通知を取得し、必要に応じて、デバッグ用のアプリケーションにアタッチする必要があるホストを作成する場合 `IActiveScriptSiteDebug` のインターフェイスとともにこのインターフェイスを実装します。  プロセス デバッグ マネージャーは `IActiveScriptDebug` して Just\-In\-Time なスクリプト デバッガーがコンピューターに存在する場合を通知します。  Just\-In\-Time スクリプト デバッガーがない場合、PDM は `IActiveScriptDebugEx` によって通知を提供します。  
  
 ランタイム エラーの通知を取得するには、ホストは [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/ja-jp/cf7639f9-a699-4571-9f3a-82ef52c0b5f4)を処理する必要があります。  ユーザー アクションに基づいて、内部デバッガーと戻り値をアタッチするか、OnScriptErrorDebug `pfEnterDebugger` のパラメーターのデバッガーの起動を返すように決定できます。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|プロセス デバッグ マネージャーで時間のデバッガーの外部エラーが検出されない場合、スクリプトの実行時エラーについてホストに通知します。|