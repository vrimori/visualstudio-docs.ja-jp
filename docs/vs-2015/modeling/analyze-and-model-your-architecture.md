---
title: 分析し、モデルのアーキテクチャ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1b7d7f9f478e85229eaa72ab04d12b6b542cbab5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781037"
---
# <a name="analyze-and-model-your-architecture"></a>アーキテクチャを分析およびモデルする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio アーキテクチャおよびモデリング ツールを使用してアプリを設計およびモデル化することによって、ユーザー要件を満たすアプリを作成できます。 Visual Studio を使用してコードの構造、動作、および関係を視覚化することによって、既存のプログラム コードを容易に理解できるようになります。  
  
 開発プロセスの一部として、アプリケーション ライフサイクル全体においてさまざまな詳細レベルでモデルを作成できます。 Team Foundation Server の作業項目と自分の開発計画にモデル要素をリンクすることによって、モデルに関連付けられた要件、タスク、テスト ケース、バグ、およびその他の作業を追跡できます。 参照してください[シナリオ: 視覚化を使用して、モデリングおよびデザインの変更](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)します。  
  
 各機能をサポートする Visual Studio のバージョンを確認するには、「 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
## <a name="to"></a>終了  
  
|||  
|-|-|  
|**コードの視覚化**:<br /><br /> -コード マップを作成して、コードの編成や関係を参照します。 アセンブリ、名前空間、クラス、メソッドなどの間の依存関係を視覚化します。<br />-コードからクラス ダイアグラムを作成して、クラスの構造と、特定のプロジェクト メンバーを参照します。<br />-コードを検証するレイヤー図を作成して、コードと設計の間の競合を検索します。<br /><br /> **注**: Visual Studio のこのリリースでは、 *依存関係グラフ* の代わりに、 *コード マップ*という用語を使用します。 一般的に、 *グラフ* という用語が単独で使用される場合は、有向グラフまたは DGML 図 (またはドキュメント) を表します。 コード マップは、DGML 図の特化された型です。|-   [コードの視覚化](../modeling/visualize-code.md)<br />-   [クラスとその他の型 (クラス デザイナー) の使用](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [ビデオ: 視覚化 (チャネル 9) によるコードの依存関係を理解します。](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [ビデオ: 視覚化 (チャネル 9) の変更の影響](http://go.microsoft.com/fwlink/?LinkID=252068)|  
|**ユーザーの要求を記述して伝達する**:<br /><br /> -ユーザー ストーリー、ビジネス ルール、およびその他の要件を明確にし、ユース ケース、アクティビティ、およびクラス図などの UML 図を描画して一貫性を確保します。|-   [アプリのモデルを作成します。](../modeling/create-models-for-your-app.md)<br />-   [ユーザー要件のモデリング](../modeling/model-user-requirements.md)<br />-   [ビデオ: モデリング (チャネル 9) によるアーキテクチャを改善します。](http://go.microsoft.com/fwlink/?LinkID=252078)|  
|**アーキテクチャを定義する**:<br /><br /> -UML コンポーネント、クラス、およびシーケンス図を描画することで、ソフトウェア システムおよびデザイン パターンの大規模な構造をモデルします。<br />-定義し、レイヤー図を作成して、コードのコンポーネント間の依存関係に制約を適用します。|-   [アプリのモデルを作成します。](../modeling/create-models-for-your-app.md)<br />-   [アプリのアーキテクチャをモデル化します。](../modeling/model-your-app-s-architecture.md)<br />-   [ビデオ: モデリング (チャネル 9) によるアーキテクチャを改善します。](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [ビデオ: レイヤー図を使用して、設計と検証 (チャネル 9)、アーキテクチャ](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**要求と、必要とされる設計を照らし合わせてシステムを検証する:**<br /><br /> -受け入れテストや、要件モデルに基づくシステム テストを定義します。 これにより、テストとユーザーの要求との間に強固な関係が生成され、要求が変更された場合にシステムをより簡単に更新できます。<br />アーキテクチャを記述するレイヤー図でコードの依存関係を検証し、設計と競合する変更を防止します。|-   [開発中にシステムを検証します。](../modeling/validate-your-system-during-development.md)<br />-   [ビデオ: レイヤー図を使用して、設計と検証 (チャネル 9)、アーキテクチャ](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Team Foundation バージョン コントロールを使用してモデル、図、およびコード マップを共有する**:<br /><br /> -コード マップ、モデリングと共有できるように、プロジェクト、UML 図、および Team Foundation バージョン管理下のレイヤー図を配置します。|Team Foundation のバージョン コントロール下でこれらの項目を使用するユーザーが複数いる場合は、バージョン管理の問題を回避するために、次のガイドラインを使用します。<br /><br /> -   [モデルと図のバージョン管理を管理します。](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**UML 言語やドメイン固有の言語から、アプリケーションの各部分を生成または構成する**:<br /><br /> -デザインする要件の変更に応答性を高めると変数を簡単に、製品ラインの間で。|-   [生成し、モデルからのアプリの構成](../modeling/generate-and-configure-your-app-from-models.md)|  
|**モデルと図をカスタマイズする**:<br /><br /> -方法、プロジェクトで使用して、UML 要素、モデルが、ビジネス ルール、および追加のメニュー コマンドとツールボックス項目に準拠しているかどうかを確認する検証制約の追加のプロパティを定義することでモデルを適合させます。<br />-独自のドメイン固有言語を作成します。|-   [UML モデルと図を拡張します。](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**T4 テンプレートを使用してテキストを生成する**:<br /><br /> -テキスト ベースのファイルを生成するのにテキスト ブロックとテンプレートの内部制御ロジックを使用します。|-   [コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)|  
  
## <a name="types-of-models-and-their-uses"></a>モデルの種類とその用途  
  
|**モデルの種類と一般的な用途**|  
|-------------------------------------|  
|**コード マップ**<br /><br /> コード マップは、コードの編成や関係を理解するために役立ちます。<br /><br /> 一般的な用途:<br /><br /> -プログラムのコードを調べるため、その構造とその依存関係をより深く理解することができます、更新、およびのコストを見積もる方法で提案された変更。<br /><br /> 参照トピック<br /><br /> -   [ソリューション間の依存関係をマップします。](../modeling/map-dependencies-across-your-solutions.md)<br />-   [アプリケーションをデバッグするコード マップの使用](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [コード マップ アナライザーを使った潜在的な問題を検索します。](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**レイヤー図**<br /><br /> レイヤー図を使用すると、アプリケーションの構造を一連のレイヤーまたは明示的な依存関係があるブロックとして定義できます。 検証を実行すると、コード内の依存関係と、レイヤー図で説明された依存関係の競合を検出できます。<br /><br /> 一般的な用途:<br /><br /> -ライフ サイクルを通じて多数の変更、アプリケーションの構造を安定化します。<br />コードの変更をチェックインする前に意図しない依存関係の競合を検出します。<br /><br /> 参照トピック<br /><br /> -   [コードからレイヤー図を作成します。](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [レイヤー図: リファレンス](../modeling/layer-diagrams-reference.md)<br />-   [レイヤー図を使用したコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)|  
|**UML モデル**<br /><br /> UML モデルには、クラス図、コンポーネント図、ユース ケース図、アクティビティ図、シーケンス図など、いくつかのビューが含まれます。 UML は、アプリケーション ドメインに合わせてカスタマイズできます。 たとえば、タグ、追加情報、および制約をモデル要素にアタッチできます。 モデルを操作するツールを定義することもできます。 参照してください[アプリのモデルを作成する](../modeling/create-models-for-your-app.md)します。<br /><br /> 一般的な用途:<br /><br /> 要件とデザインについて説明します。 UML は、あらゆるアプリケーションの開発にすばやく適用できます。 参照してください[モデルを使用して、開発プロセスで](../modeling/use-models-in-your-development-process.md)します。<br />-生成またはテストまたはアプリケーションの部分を構成します。 表記法のカスタマイズと生成テンプレートまたは構成可能アプリケーションの開発には、いくらかの作業が必要です。 参照してください[生成モデルからアプリを構成および](../modeling/generate-and-configure-your-app-from-models.md)します。<br />-一般的な説明とコードの生成または小規模なプロジェクトで構成します。|  
|**ドメイン固有言語 (DSL)**<br /><br /> DSL は、特定の目的のために設計する表記法です。 Visual Studio では、通常、グラフィックです。<br /><br /> 一般的な用途:<br /><br /> 生成またはアプリケーションのパーツを構成します。 表記法およびツールを開発するには、作業が必要です。 これを行うと、UML のカスタマイズよりもドメインに適合する結果となることがあります。<br />-の大規模なプロジェクトまたは製品ラインの 1 つ以上のプロジェクトで使用することで、DSL とそのツールの開発への投資が返されます。<br /><br /> 参照トピック<br /><br /> -   [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>情報の入手方法  
  
|||  
|-|-|  
|**フォーラム**|-   [Visual Studio の視覚化ツールとモデリング ツール](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio の視覚化およびモデリング SDK (DSL ツール)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>関連項目  
 [新機能](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps とアプリケーション ライフサイクル管理](http://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)



