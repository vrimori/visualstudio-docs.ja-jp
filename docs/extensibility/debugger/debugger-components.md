---
title: "デバッガーのコンポーネント |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec2b7a18dac9616db1743a50539c2860caca2e26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debugger-components"></a>デバッガー コンポーネント
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッガーが VSPackage として実装され、全体のデバッグ セッションを管理します。 デバッグ セッションには、次の要素が構成されています。  
  
-   **デバッグ パッケージ:** 、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッガーの新機能は、デバッグ中に関係なく同じユーザー インターフェイスを提供します。  
  
-   **セッション デバッグ マネージャー (SDM):**に一貫性のあるプログラム インターフェイスを提供、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]さまざまなデバッグ エンジンの管理用のデバッガーです。 によって実装されている[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
-   **プロセスのデバッグ マネージャー (PDM):**のすべての実行中インスタンスの管理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、またはデバッグ中のすべてのプログラムの一覧です。 によって実装されている[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
-   **デバッグ エンジン (DE):**をデバッグするプログラムの監視のリアルタイム分析を提供するには、式エバリュエーターとシンボルのプロバイダーと対話すると、SDM と、PDM を実行中のプログラムの状態を通信して、プログラムのメモリと変数の状態です。 によって実装されている[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](のサポート言語) およびサード パーティ ベンダーが独自の実行時間をサポートします。  
  
-   **式エバリュエーター (EE):**変数と、プログラムが特定の時点で停止された時に、ユーザーが指定の式を動的に評価するためのサポートを提供します。 によって実装されている[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](のサポート言語) およびサード パーティ ベンダーが独自の言語をサポートします。  
  
-   **シンボル プロバイダー (SP):**とも呼ばれるシンボル ハンドラーでは、マップ、プログラムのデバッグ シンボル、プログラムの実行中のインスタンスに (ソース コード レベルのデバッグ、式の評価) など意味のある情報を指定することができるようにします。 によって実装されている[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](共通言語ランタイム [CLR] のシンボルと、プログラム データベース [PDB] シンボル ファイルの形式) と、デバッグ情報を格納するが自分独自のメソッドが含まれているサード パーティ ベンダーによってです。  
  
 次の図は、Visual Studio デバッガーのこれらの要素間の関係を示します。  
  
 ![コンポーネント デバッグの概要](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>このセクションの内容  
 [パッケージのデバッグ](../../extensibility/debugger/debug-package.md)  
 実行するデバッグ パッケージについて説明します、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]シェルし、すべての UI を処理します。  
  
 [プロセス デバッグ マネージャー](../../extensibility/debugger/process-debug-manager.md)  
 デバッグ可能なプロセスの管理者であると、PDM の機能の概要を示します。  
  
 [セッション デバッグ マネージャー](../../extensibility/debugger/session-debug-manager.md)  
 IDE に、デバッグ セッションの統一されたビューを提供すると、SDM を定義します。 SDM デを管理します。  
  
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)  
 デが提供するデバッグ サービスをについて説明します。  
  
 [操作モード](../../extensibility/debugger/operational-modes.md)  
 IDE の操作に使用できる 3 つのモードの概要を説明します。 デザイン モード、実行モードと中断モード。 移行方法についても説明します。  
  
 [式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)  
 実行時に、EE の目的を説明します。  
  
 [シンボル プロバイダー](../../extensibility/debugger/symbol-provider.md)  
 方法については、実装にシンボル プロバイダー評価変数および式について説明します。  
  
 [型のビジュアライザーとカスタム ビューアー](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 新機能について説明します型のビジュアライザーとカスタム ビューアーがあり、どのような役割の両方をサポートする、式エバリュエーターを再生します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャ、主要な概念をについて説明します。  
  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 デの動作方法に同時にコード、ドキュメント、および式の評価のコンテキスト内でについて説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式を評価するなど、さまざまなデバッグ タスクへのリンクが含まれています。  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)