---
title: ワークフロー デザイナーを使用したアプリケーションの開発 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6a010a0df75e683ad26ac0ca297a0ab817bd22cd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533656"
---
# <a name="developing-applications-with-the-workflow-designer"></a>ワークフロー デザイナーを使用したアプリケーションの開発
[!INCLUDE[wfd1](../includes/wfd1-md.md)]は、[!INCLUDE[wf](../includes/wf-md.md)] 開発環境内でホストされる [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] 内の [!INCLUDE[vs2010](../includes/vs2010-md.md)] アプリケーションをグラフィカルに作成してデバッグするためのビジュアルなデザイナーおよびデバッガーです。 テンプレートおよびアクティビティ デザイナーを使用して、複合ワークフロー アプリケーション、アクティビティ ライブラリ、または [!INCLUDE[indigo1](../includes/indigo1-md.md)] サービスを作成できます。 [!INCLUDE[crabout](../includes/crabout-md.md)] ワークフローを参照してください、 [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66)します。  
  
 以前のバージョンの[!INCLUDE[wfd2](../includes/wfd2-md.md)]に追加された、この新バージョンの[!INCLUDE[wfd2](../includes/wfd2-md.md)]のデザイン機能を次に示します。  
  
-   [!INCLUDE[wfd2](../includes/wfd2-md.md)]は、[!INCLUDE[avalon1](../includes/avalon1-md.md)] を使用して構築されています。 これにより、アクティビティ デザイナーのエクスペリエンスが向上し、大規模で複雑なワークフローに対するパフォーマンスが改善されます。  
  
-   カスタム アクティビティを、[!INCLUDE[avalon2](../includes/avalon2-md.md)] で XAML を使用してデザインできます。また、アクティビティ デザイナーを作成するためのプログラミング モデルが単純化されています。  
  
-   Flowchart アクティビティの実装により、一般的なフローチャート モデル化スタイルを使用して、プログラム フローを視覚的に表現できます。  
  
-   [!INCLUDE[wfd2](../includes/wfd2-md.md)]の新しい変数デザイナーにより、ワークフロー内の変数を宣言してスコープを設定し、アクティビティにバインドできます。  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)] では、[!INCLUDE[wfd2](../includes/wfd2-md.md)] ワークフロー内で Visual Basic 式を作成するときに、[!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]で IntelliSense の機能をすべて利用できます。  
  
-   デバッグ用の機能が XAML にも拡張されているため、XAML ワークフロー定義にブレークポイントを設定して、実行時に XAML コードにステップ インすることができます。ここでは、マネージ コードを扱う場合と同じように操作できます。  
  
-   [!INCLUDE[wfd2](../includes/wfd2-md.md)] の外側での[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]の再ホストが、以前のバージョンに比べて大幅に簡略化され、数行のコードのみになりました。  
  
-   新しい<xref:System.Activities.Statements.Flowchart>アクティビティとその[フローチャート](../workflow-designer/flowchart-activity-designer.md)使い慣れたフローチャートをモデル化スタイルを使用して、プログラム フローを視覚化することです。  
  
-   メッセージング アクティビティが強化されているため、完全な宣言型の (コードなし) [!INCLUDE[indigo1](../includes/indigo1-md.md)] サービスを記述できます。  
  
-   **サービス参照を追加しています.** 機能を使用すると、自動的に Web サービスにアクセスするアクティビティを生成できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ワークフロー デザイナーの使用](../workflow-designer/using-the-workflow-designer.md)  
 組み込みのデザイナーを使用して新しいアクティビティおよびワークフロー プロジェクトを作成する方法と、デザイナーが備えているその他のツールを使用して、引数、変数、式、インポート、および階層リンク ナビゲーションを処理する方法について説明します。  
  
 [アクティビティ デザイナーの使用](../workflow-designer/using-the-activity-designers.md)  
 アクティビティとテンプレートのカテゴリ、およびそれらのシステム標準のデザイナーについて説明します。  
  
 [ワークフロー デザイナーを使用したワークフローのデバッグ](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 従来のデバッグ手順に加えて、XAML および式のデバッグを行う方法について説明します。  
  
 [ワークフロー デザイナーの UI ヘルプ](../workflow-designer/workflow-designer-ui-help.md)  
 [!INCLUDE[wfd1](../includes/wfd1-md.md)]で表示されるダイアログ ボックスの状況依存のヘルプ トピックについて説明し、デザイナーのシェルの機能、ショートカット キー、およびエラー メッセージに関するガイダンスを示します。  
  
 [.NET 3.0 または .NET 3.5 Framework を対象とするワークフロー アプリケーションの開発](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] または [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] を対象とする従来のデザイナーの使用方法に関するガイダンスを示します。  
  
 [デザイナーのホスト変更&#91;WF のサンプル&#93;](http://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 このサンプルは、デザイナーを含む WPF レイアウトを作成する方法を示します。  
  
 [カスタム アクティビティ デザイナー](http://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075)  
 このセクションでは、ワークフロー デザイナーに表示するカスタム デザイナーを使用するアクティビティ サンプルを示します。