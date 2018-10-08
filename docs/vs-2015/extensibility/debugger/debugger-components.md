---
title: デバッガーのコンポーネント |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b1b8f12a8bfa15a352f38d021a64a6f9f8b9244
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536944"
---
# <a name="debugger-components"></a>デバッガーのコンポーネント
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[デバッガー コンポーネント](https://docs.microsoft.com/visualstudio/extensibility/debugger/debugger-components)します。  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]デバッガーは、VSPackage として実装され、全体のデバッグ セッションを管理します。 デバッグ セッションには、次の要素が構成されています。  
  
-   **パッケージのデバッグ:** 、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]デバッガーがデバッグ中に関係なく同じユーザー インターフェイスを提供します。  
  
-   **セッション デバッグ マネージャー (SDM):** に一貫性のあるプログラム インターフェイスを提供、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]さまざまなデバッグ エンジンの管理用のデバッガーです。 によって実装されている[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
-   **プロセス デバッグ マネージャー (PDM):** 管理、実行中のすべてのインスタンスの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、またはデバッグ中のすべてのプログラムの一覧。 によって実装されている[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
-   **デバッグ エンジン (DE):** のデバッグ中のプログラムを監視、SDM を PDM は、実行中のプログラムの状態との相互作用のリアルタイム分析を提供するには、式エバリュエーターとシンボル プロバイダー、プログラムのメモリと変数の状態。 によって実装されます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)](の対応言語) と、独自のランタイムをサポートするサード パーティ ベンダー。  
  
-   **式エバリュエーター (EE):** 変数と、プログラムが特定の時点で停止したときに、ユーザーが指定した式を動的に評価するためのサポートを提供します。 によって実装されます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)](の対応言語) とは自分の言語をサポートするサード パーティ ベンダー。  
  
-   **シンボル プロバイダー (SP):** とも呼ばれるシンボル ハンドラーでは、プログラムのデバッグ シンボルにマップ、プログラムの実行中のインスタンス (ソース コード レベルのデバッグ、式の評価) など意味のある情報を提供できるようにします。 によって実装されている[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)](共通言語ランタイム [CLR] のシンボルと [PDB] プログラム データベース シンボル ファイルの形式)、デバッグ情報を保存する独自の専用メソッドを持つサード パーティ ベンダー。  
  
 次の図は、Visual Studio デバッガーのこれらの要素間の関係を示します。  
  
 ![コンポーネント デバッグの概要](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>このセクションの内容  
 [パッケージのデバッグ](../../extensibility/debugger/debug-package.md)  
 実行されるデバッグ パッケージについて説明します、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]シェルし、すべての UI を処理します。  
  
 [プロセス デバッグ マネージャー](../../extensibility/debugger/process-debug-manager.md)  
 デバッグ可能なプロセス マネージャーであると、PDM の機能の概要を示します。  
  
 [セッション デバッグ マネージャー](../../extensibility/debugger/session-debug-manager.md)  
 IDE、デバッグ セッションの統合ビューを提供すると、SDM を定義します。 SDM は、DE を管理します。  
  
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)  
 デバッグ、DE を提供するサービスについて説明します。  
  
 [操作モード](../../extensibility/debugger/operational-modes.md)  
 IDE の操作に使用できる 3 つのモードの概要を説明します。 デザイン モード、実行モードと中断モード。 移行方法についても説明します。  
  
 [式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)  
 実行時に、EE の目的について説明します。  
  
 [シンボル プロバイダー](../../extensibility/debugger/symbol-provider.md)  
 方法については、実装、シンボル プロバイダー評価変数よぶ式について説明します。  
  
 [型のビジュアライザーとカスタム ビューアー](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 について説明します型のビジュアライザーおよびカスタム ビューアーし、どのような役割の両方をサポートしている、式エバリュエーターを再生します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャの主要な概念をについて説明します。  
  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 コード、ドキュメント、および式の評価のコンテキスト内で、DE がどの同時に動作について説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式の評価などのさまざまなデバッグ タスクへのリンクが含まれています。  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

