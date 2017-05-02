---
title: "アクティブ スクリプト プロファイリングの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アクティブ スクリプト プロファイリング"
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# アクティブ スクリプト プロファイリングの概要
[アクティブ スクリプト プロファイラーのインターフェイス](../winscript/reference/active-script-profiler-interfaces.md) は、スクリプト エンジンのプロファイリングを有効にします。  アクティブ スクリプトのプロファイルは次の要素から構成されます:  
  
-   言語のエンジン  
  
-   ホスト  
  
-   プロファイラー  
  
## 言語のエンジン  
 言語のスクリプト エンジンはを実装します。  これは、実装としてスクリプト コードのプロファイリングを有効にするメソッドを提供します。  プロファイリングを有効にすると、言語のエンジンは、引数としてプロファイラー COM オブジェクトのクラス ID \(CLSID\) を受け取ります。  次に、プロファイラーにさまざまなイベントが発生すると、プロファイラー COM オブジェクトと呼び出しのインスタンスを作成します。  
  
 言語のエンジンは [IActiveScriptProfilerControl インターフェイス](../winscript/reference/iactivescriptprofilercontrol-interface.md)\) を実装します。  
  
> [!NOTE]
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の言語ランタイムは、プロファイリングを有効にするかどうかを決定するために作成 JS\_PROFILER の環境変数がチェックされます。  この変数がプロファイラーの CLSID に設定されている場合、言語ランタイムが変数の値を使用して作成するプロファイラーを決定するためにプロファイラー COM オブジェクトのインスタンスを作成します。  
  
## ホスト  
 ホストは、言語のエンジンを作成し、実行されるスクリプト言語をエンジンに提供します。  スマート ホストは、デバッグまたはプロファイリングを行うときにより詳細な情報を提供するために、デバッガー、プロファイラーで使用できるドキュメントのコンテキストを提供します。  
  
## プロファイラー  
 プロファイラーは、さまざまなイベントが発生すると、言語のエンジンからの呼び出しを受け取ります。  プロファイラーは、COM オブジェクトとして登録され、[IActiveScriptProfilerCallback インターフェイス](../winscript/reference/iactivescriptprofilercallback-interface.md)\) のインターフェイスを実装する必要があります。  
  
## 参照  
 [アクティブ スクリプト プロファイラーのインターフェイス](../winscript/reference/active-script-profiler-interfaces.md)