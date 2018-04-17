---
title: 分析およびモデルのアーキテクチャ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-modeling
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 174468e1219533faf74f3b88f1b56aa084889291
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="analyze-and-model-your-architecture"></a>アーキテクチャを分析およびモデルする
アプリが Visual Studio アーキテクチャを使用するツールとモデリング ツールを設計およびアプリのモデルによってアーキテクチャの要件を満たしていることを確認してください。

* Visual Studio を使用してコードの構造、動作、および関係を視覚化することによって、既存のプログラム コードを容易に理解できるようになります。

* アーキテクチャの依存関係を考慮し、必要でチームを教育します。  

* 開発プロセスの一部として、アプリケーション ライフサイクル全体においてさまざまな詳細レベルでモデルを作成できます。

参照してください[シナリオ: 視覚化を使用するツールとモデリング デザインの変更](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)です。  

## <a name="to"></a>終了  

|||  
|-|-|  
|**コードの視覚化**:<br /><br /> -コード マップを作成することで、コードの編成や関係を参照します。 アセンブリ、名前空間、クラス、メソッドなどの間の依存関係を視覚化します。<br />-コードからクラス図を作成することで、クラス構造体と特定のプロジェクトのメンバーを参照します。<br />コードを検証する依存関係図を作成して、コードと設計の間の競合を検索します。|-   [コードの視覚化](../modeling/visualize-code.md)<br />-   [クラスとその他の種類 (クラス デザイナー) の使用](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [ビデオ: Visual Studio 2015 コード マップでコードが設計を理解します。](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [ビデオ: リアルタイムで、アーキテクチャの依存関係を検証します。](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**アーキテクチャを定義する**:<br /><br /> -定義し、依存関係図を作成して、コードのコンポーネント間の依存関係の制約を適用します。|-   [ビデオ: Visual Studio (チャネル 9) とアーキテクチャの依存関係を検証します。](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**要求と、必要とされる設計を照らし合わせてシステムを検証する:**<br /><br /> アーキテクチャを記述する依存関係図でコードの依存関係を検証し、設計と競合する変更を防止します。|-   [ビデオ: Visual Studio (チャネル 9) とアーキテクチャの依存関係を検証します。](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Team Foundation バージョン コントロールを使用してモデル、図、およびコード マップを共有する**:<br /><br /> -コード マップ、および配置するプロジェクトでは、Team Foundation バージョン管理下にある deoendency ダイアグラムそれらを共有できるようにします。| |  
|**モデルと図をカスタマイズする**:<br /><br /> -独自のドメイン固有言語を作成します。|-   [Visual Studio - ドメイン固有言語のモデリング SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**T4 テンプレートを使用してテキストを生成する**:<br /><br /> -テキスト ベースのファイルを生成するのに、テキスト ブロックとテンプレート内部制御ロジックを使用します。<br /> の Visual Studio に含まれる MSBuild で T4 テンプレート ビルド|-   [コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)|

各機能をサポートする Visual Studio のバージョンを確認するには、「 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  

## <a name="types-of-models-and-their-uses"></a>モデルの種類とその用途  

|**モデルの種類と一般的な用途**|  
|-------------------------------------|  
|**コード マップ**<br /><br /> コード マップは、コードの編成や関係を理解するために役立ちます。<br /><br /> 一般的な用途:<br /><br /> -プログラム コードを調べるため、その構造とその依存関係をより深く理解することができます、更新、およびのコストを推定する方法、提案された変更します。<br /><br /> 参照トピック<br /><br /> -   [ソリューション間の依存関係をマップします。](../modeling/map-dependencies-across-your-solutions.md)<br />-   [コード マップを使用してアプリケーションをデバッグするには](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [コード マップ アナライザーを使用して潜在的な問題を検索します。](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**依存関係図**<br /><br /> 依存関係の図では、レイヤーまたは明示的な依存関係があるブロックのセットとして、アプリケーションの構造を定義できます。 コード内の依存関係と依存関係図で説明された依存関係の競合を検出する検証を実行することができます。<br /><br /> 一般的な用途:<br /><br /> -、ライフ サイクルを通じて多数の変更を使用して、アプリケーションの構造を安定化します。<br />-コードに変更をチェックインする前に、意図しない依存関係の競合を検出します。<br /><br /> 参照トピック<br /><br /> -   [コードから依存関係のダイアグラムを作成します。](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)<br />-   [依存関係のダイアグラムのコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)|  
|**ドメイン固有言語 (DSL)**<br /><br /> DSL は、特定の目的のために設計する表記法です。 Visual Studio では、通常、グラフィックです。<br /><br /> 一般的な用途:<br /><br /> 生成またはアプリケーションの部分を構成します。 表記法およびツールを開発するには、作業が必要です。 これを行うと、UML のカスタマイズよりもドメインに適合する結果となることがあります。<br />-大規模プロジェクトまたは製品ラインの複数のプロジェクトで使用して、DSL やそのツールと開発への投資が返されます。<br /><br /> 参照トピック<br /><br /> -   [Visual Studio - ドメイン固有言語のモデリング SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  

## <a name="where-can-i-get-more-information"></a>情報の入手方法  

[Visual Studio の視覚化およびモデリング ツールのフォーラム](http://go.microsoft.com/fwlink/?LinkId=184720)  

## <a name="see-also"></a>関連項目  
 [新機能します。](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps とアプリケーション ライフ サイクル管理](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
