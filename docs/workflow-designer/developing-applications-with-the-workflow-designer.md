---
title: ワークフロー デザイナーを使用したアプリケーションの開発
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecc9e42146bfa7de259551ff1c90d27201db5725
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970126"
---
# <a name="developing-applications-with-the-workflow-designer"></a>ワークフロー デザイナーを使用したアプリケーションの開発

Windows ワークフロー デザイナーは、ビジュアル デザイナーでグラフィカルに作成して、Visual Studio 2010 の開発環境でホストされている .NET Framework 4 で Windows Workflow Foundation (WF) アプリケーションのデバッグ用のデバッガー。 複合ワークフロー アプリケーション、アクティビティ ライブラリ、またはテンプレートおよびアクティビティ デザイナーを使用して Windows Communication Foundation (WCF) サービスを作成することができます。 ワークフローの詳細については、次を参照してください。、 [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66)です。

 ワークフロー デザイナーの古いバージョンとは別に、ワークフロー デザイナーのこの新しいバージョンを設定するいくつかの新しいデザイン機能を次に示します。

-   ワークフロー デザイナーは、Windows Presentation Foundation (WPF) を使用して作成されています。 これにより、アクティビティ デザイナーのエクスペリエンスが向上し、大規模で複雑なワークフローに対するパフォーマンスが改善されます。

-   カスタム アクティビティを、[!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)] で XAML を使用してデザインできます。また、アクティビティ デザイナーを作成するためのプログラミング モデルが単純化されています。

-   Flowchart アクティビティの実装により、一般的なフローチャート モデル化スタイルを使用して、プログラム フローを視覚的に表現できます。

-   ワークフロー デザイナーは、新しい変数デザイナーを宣言し、ワークフロー内の変数のスコープをアクティビティにバインドします。

-   Visual Studio 2010 では、ワークフロー デザイナーは、.NET Framework 4 ワークフロー内の Visual Basic 式を作成するときにすべての IntelliSense 機能を提供します。

-   デバッグ用の機能が XAML にも拡張されているため、XAML ワークフロー定義にブレークポイントを設定して、実行時に XAML コードにステップ インすることができます。ここでは、マネージ コードを扱う場合と同じように操作できます。

-   Visual Studio の外部でワークフロー デザイナーを再ホストが大幅に簡略化と比較して以前のバージョンでのみ、数行のコードを必要とするようになりました。

-   新しい<xref:System.Activities.Statements.Flowchart>アクティビティとその[フローチャート](../workflow-designer/flowchart-activity-designer.md)使い慣れたフローチャートをモデル化スタイルを使用して、プログラム フローを視覚化することです。

-   メッセージング アクティビティが強化された、許可を記述する完全な宣言型コードではなく Windows Communication Foundation (WCF) サービス。

-   **サービス参照を追加しています.** 機能では、自動的に Web サービスにアクセスするアクティビティを生成することができます。