---
title: "アクティブ スクリプト プロファイリングの概要 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9413e8b6e6db0c81eb1853c24506d20c8d06f3e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-profiling-overview"></a>アクティブ スクリプト プロファイリングの概要
[アクティブ スクリプト プロファイラーのインターフェイス](../winscript/reference/active-script-profiler-interfaces.md)は、スクリプト エンジンのプロファイリングを有効にします。 アクティブ スクリプト プロファイリングは次の要素から構成されます。  
  
-   言語エンジン  
  
-   ホスト  
  
-   プロファイラー  
  
## <a name="language-engine"></a>言語エンジン  
 言語エンジンはスクリプトを実行します。 言語エンジンでは、実行時にスクリプト コードのプロファイリングを有効にするメソッドが提供されています。 プロファイリングを有効にすると、言語エンジンはプロファイラー COM オブジェクトのクラス ID (CLSID) を引数として受け取ります。 言語エンジンは、プロファイラー COM オブジェクトのインスタンスを作成し、さまざまなイベントが発生するとプロファイラーを呼び出します。  
  
 言語エンジンは、[IActiveScriptProfilerControl インターフェイス](../winscript/reference/iactivescriptprofilercontrol-interface.md)を実装しています。  
  
> [!NOTE]
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の言語ランタイムは、作成時に JS_PROFILER 環境変数を調べて、プロファイリングを有効にするかどうかを判断します。 この変数にプロファイラーの CLSID が設定されている場合、言語ランタイムは、変数の値を使って作成するプロファイラーを特定して、プロファイラー COM オブジェクトのインスタンスを作成します。  
  
## <a name="host"></a>ホスト  
 ホストは、言語エンジンを作成し、実行するスクリプトを言語エンジンに提供します。 また、スマート ホストは、デバッグ時またはプロファイリング時により詳細な情報を提供できるように、デバッガーまたはプロファイラーが使うことのできるドキュメント コンテキストを提供します。  
  
## <a name="profiler"></a>プロファイラー  
 プロファイラーは、さまざまなイベントが発生すると、言語エンジンから呼び出しを受け取ります。 プロファイラーは、COM オブジェクトとして登録され、[IActiveScriptProfilerCallback インターフェイス](../winscript/reference/iactivescriptprofilercallback-interface.md)を実装している必要があります。  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト プロファイラーのインターフェイス](../winscript/reference/active-script-profiler-interfaces.md)