---
title: コードの視覚化
ms.date: 11/04/2016
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c1061d7369bbd73232ceb15dd71db203ee392da
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="visualize-code"></a>コードの視覚化
Visual Studio の視覚化ツールとモデリング ツールを使って、既存のコードを理解し、アプリケーションを記述することができます。 これにより、自分が実行した変更がコードにどのような影響を与えるかを理解し、その変更に起因する作業とリスクを評価することができます。 例:

-   コード内のリレーションシップを理解するには、そのリレーションシップをビジュアルにマッピングします。

-   システムのアーキテクチャについて説明し、コードの設計と一貫性を維持、依存関係のダイアグラムを作成し、これらの図と照らし合わせてコードを検証します。

-   クラス構造を記述するには、クラス ダイアグラムを作成します。

 またこれらのツールを使用すると、プロジェクトの関係者と簡単にやり取りすることができます。

 各機能をサポートする Visual Studio のバージョンを確認するには、「 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。

## <a name="what-do-you-want-to-do"></a>実行する操作

|||
|-|-|
|**コードとの関係を理解します。**<br /><br /> 特定のコード間のリレーションシップをマッピングします。<br /><br /> ソリューション全体のコード内のリレーションシップの概要を確認します。<br /><br /> **注**: Visual Studio のこのリリースでは、 *依存関係グラフ* の代わりに、 *コード マップ*という用語を使用します。|-   [ソリューション間の依存関係をマップします。](../modeling/map-dependencies-across-your-solutions.md)<br />-   [コード マップを使用してアプリケーションをデバッグするには](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [コード マップ アナライザーを使用して潜在的な問題を検索します。](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [デバッグ中に、呼び出し履歴に対するメソッドをマップします。](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**クラス構造を理解するには。**<br /><br /> コードからクラス ダイアグラムを作成することで、プロジェクト内のクラスの構造を視覚化します。|[方法: プロジェクトにクラス ダイアグラムを追加する (クラス デザイナー)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**高度なシステムの設計について説明し、コードこの設計に照らし合わせて検証します。**<br /><br /> 依存関係図を作成して、高度なシステムの設計と、目的の依存関係を説明します。 このデザインと照らし合わせてコードを検証し、コード内の依存関係がデザインと一貫性があることを確認します。|-   [コードから依存関係のダイアグラムを作成します。](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)<br />-   [依存関係図: ガイドライン](../modeling/layer-diagrams-guidelines.md)<br />-   [依存関係のダイアグラムのコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>外部リソース

|**カテゴリ**|**Links**|
|------------------|---------------|
|**フォーラム**|-   [Visual Studio の視覚化ツールとモデリング ツール](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio の視覚化ツールとモデリング SDK (DSL ツール)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**ブログ**|[Visual Studio ALM + Team Foundation Server のブログ](http://go.microsoft.com/fwlink/?LinkID=201340)|
|**技術記事とジャーナル**|[MSDN アーキテクチャ フォーラム](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>関連項目

- [シナリオ: 視覚化およびモデリングを使用したデザインの変更](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [アーキテクチャの分析およびモデリング](../modeling/analyze-and-model-your-architecture.md)
- [アプリのアーキテクチャをモデル化する](../modeling/model-your-app-s-architecture.md)
- [開発プロセス内でのモデルの使用](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
