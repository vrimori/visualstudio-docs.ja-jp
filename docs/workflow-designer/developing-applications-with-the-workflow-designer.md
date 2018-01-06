---
title: "ワークフロー デザイナーでアプリケーションの開発 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "17"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 61d58b172c185a908a6314664ccd4cfe2172dc8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="developing-applications-with-the-workflow-designer"></a>ワークフロー デザイナーを使用したアプリケーションの開発
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]は、[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 開発環境内でホストされる [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] 内の [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] アプリケーションをグラフィカルに作成してデバッグするためのビジュアルなデザイナーおよびデバッガーです。 テンプレートおよびアクティビティ デザイナーを使用して、複合ワークフロー アプリケーション、アクティビティ ライブラリ、または [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] サービスを作成できます。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]ワークフローを参照してください、 [Windows Workflow Foundation &#91;。NET Framework 4 &#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
 以前のバージョンの[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]に追加された、この新バージョンの[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のデザイン機能を次に示します。  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]は、[!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)] を使用して構築されています。 これにより、アクティビティ デザイナーのエクスペリエンスが向上し、大規模で複雑なワークフローに対するパフォーマンスが改善されます。  
  
-   カスタム アクティビティを、[!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)] で XAML を使用してデザインできます。また、アクティビティ デザイナーを作成するためのプログラミング モデルが単純化されています。  
  
-   Flowchart アクティビティの実装により、一般的なフローチャート モデル化スタイルを使用して、プログラム フローを視覚的に表現できます。  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の新しい変数デザイナーにより、ワークフロー内の変数を宣言してスコープを設定し、アクティビティにバインドできます。  
  
-   [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] では、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] ワークフロー内で Visual Basic 式を作成するときに、[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]で IntelliSense の機能をすべて利用できます。  
  
-   デバッグ用の機能が XAML にも拡張されているため、XAML ワークフロー定義にブレークポイントを設定して、実行時に XAML コードにステップ インすることができます。ここでは、マネージ コードを扱う場合と同じように操作できます。  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] の外側での[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]の再ホストが、以前のバージョンに比べて大幅に簡略化され、数行のコードのみになりました。  
  
-   新しい<xref:System.Activities.Statements.Flowchart>アクティビティとその[フローチャート](../workflow-designer/flowchart-activity-designer.md)使い慣れたフローチャートをモデル化スタイルを使用して、プログラム フローを視覚化することです。  
  
-   メッセージング アクティビティが強化されているため、完全な宣言型の (コードなし) [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] サービスを記述できます。  
  
-   **サービス参照を追加しています.**機能では、自動的に Web サービスにアクセスするアクティビティを生成することができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ワークフロー デザイナーの使用](../workflow-designer/using-the-workflow-designer.md)  
 組み込みのデザイナーを使用して新しいアクティビティおよびワークフロー プロジェクトを作成する方法と、デザイナーが備えているその他のツールを使用して、引数、変数、式、インポート、および階層リンク ナビゲーションを処理する方法について説明します。  
  
 [アクティビティ デザイナーの使用](../workflow-designer/using-the-activity-designers.md)  
 アクティビティとテンプレートのカテゴリ、およびそれらのシステム標準のデザイナーについて説明します。  
  
 [ワークフロー デザイナーを使用したワークフローのデバッグ](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 従来のデバッグ手順に加えて、XAML および式のデバッグを行う方法について説明します。  
  
 [ワークフロー デザイナーの UI ヘルプ](../workflow-designer/workflow-designer-ui-help.md)  
 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]で表示されるダイアログ ボックスの状況依存のヘルプ トピックについて説明し、デザイナーのシェルの機能、ショートカット キー、およびエラー メッセージに関するガイダンスを示します。  
  
 [.NET 3.0 または .NET 3.5 Framework を対象とするワークフロー アプリケーションの開発](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする従来のデザイナーの使用方法に関するガイダンスを示します。  
  
 [デザイナーのホスト変更 &#91;WF のサンプル &#93;](http://msdn.microsoft.com/Library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 このサンプルは、デザイナーを含む WPF レイアウトを作成する方法を示します。  
  
 [カスタム アクティビティ デザイナー](/dotnet/framework/windows-workflow-foundation/samples/custom-activity-designers)  
 このセクションでは、ワークフロー デザイナーに表示するカスタム デザイナーを使用するアクティビティ サンプルを示します。