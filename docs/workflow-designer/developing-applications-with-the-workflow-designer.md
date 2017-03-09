---
title: "ワークフロー デザイナーを使用したアプリケーションの開発 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DefaultWorkflowDesigner"
  - "DefaultWorkflowDesigner.UI"
helpviewer_keywords: 
  - "Visual Studio 2010 ワークフロー デザイナー [WFD]"
  - "Visual Studio 2010 ワークフロー デザイナー [WFD], 概要"
  - "ワークフロー デザイナー [WFD]"
  - "ワークフロー デザイナー [WFD], 概要"
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
caps.handback.revision: 17
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ワークフロー デザイナーを使用したアプリケーションの開発
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]は、[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 開発環境内でホストされる [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] 内の [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションをグラフィカルに作成してデバッグするためのビジュアルなデザイナーおよびデバッガーです。テンプレートおよびアクティビティ デザイナーを使用して、複合ワークフロー アプリケーション、アクティビティ ライブラリ、または [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] サービスを作成できます。ワーク フロー[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[Windows Workflow Foundation](../Topic/Windows%20Workflow%20Foundation.md)」を参照してください。  
  
 以前のバージョンの[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]に追加された、この新バージョンの[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のデザイン機能を次に示します。  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]は、[!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)] を使用して構築されています。これにより、アクティビティ デザイナーのエクスペリエンスが向上し、大規模で複雑なワークフローに対するパフォーマンスが改善されます。  
  
-   カスタム アクティビティを、[!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)] で XAML を使用してデザインできます。また、アクティビティ デザイナーを作成するためのプログラミング モデルが単純化されています。  
  
-   Flowchart アクティビティの実装により、一般的なフローチャート モデル化スタイルを使用して、プログラム フローを視覚的に表現できます。  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の新しい変数デザイナーにより、ワークフロー内の変数を宣言してスコープを設定し、アクティビティにバインドできます。  
  
-   [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] では、[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] ワークフロー内で Visual Basic 式を作成するときに、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]で IntelliSense の機能をすべて利用できます。  
  
-   デバッグ用の機能が XAML にも拡張されているため、XAML ワークフロー定義にブレークポイントを設定して、実行時に XAML コードにステップ インすることができます。ここでは、マネージ コードを扱う場合と同じように操作できます。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外側での[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の再ホストが、以前のバージョンに比べて大幅に簡略化され、数行のコードのみになりました。  
  
-   新しい <xref:System.Activities.Statements.Flowchart> アクティビティおよびその [フローチャート](../workflow-designer/flowchart-activity-designer.md) により、一般的なフローチャート モデル化スタイルを使用して、プログラム フローを視覚的に表現できます。  
  
-   メッセージング アクティビティが強化されているため、完全な宣言型の \(コードなし\) [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] サービスを記述できます。  
  
-   "**サービス参照の追加**" 機能により、Web サービスにアクセスするアクティビティを自動的に生成できます。  
  
## このセクションの内容  
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
  
 [デザイナーのホスト変更 &#91;WF サンプル&#93;](../Topic/Designer%20ReHosting.md)  
 このサンプルは、デザイナーを含む WPF レイアウトを作成する方法を示します。  
  
 [カスタム アクティビティ デザイナー](../Topic/Custom%20Activity%20Designers.md)  
 このセクションでは、ワークフロー デザイナーに表示するカスタム デザイナーを使用するアクティビティ サンプルを示します。