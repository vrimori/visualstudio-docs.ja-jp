---
title: "ワークフロー デザイナーでアプリケーションの開発 |Microsoft ドキュメント"
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 75a6fb6eef1f5e8e174607ac141646ab237dd285
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>ワークフロー デザイナーを使用したアプリケーションの開発

Windows ワークフロー デザイナーは、ビジュアル デザイナーとグラフィカルに作成してデバッグ用のデバッガー[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]内のアプリケーション、[!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)]でホストされている、[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]開発環境です。 テンプレートおよびアクティビティ デザイナーを使用して、複合ワークフロー アプリケーション、アクティビティ ライブラリ、または [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] サービスを作成できます。 ワークフローの詳細については、次を参照してください。、 [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66)です。

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