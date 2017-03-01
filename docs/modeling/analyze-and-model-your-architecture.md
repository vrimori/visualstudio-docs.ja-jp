---
title: "分析およびモデルのアーキテクチャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
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
caps.latest.revision: 127
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 98d1214d1cda81102f9e03a8ce8b83886aa2c0ec
ms.openlocfilehash: 78217396085aa5531ec2cbdd5dff522201287777
ms.lasthandoff: 02/22/2017

---
# <a name="analyze-and-model-your-architecture"></a>アーキテクチャを分析およびモデルする
アプリを Visual Studio のアーキテクチャを使用し、モデリング ツールを設計して、アプリケーションのモデルのアーキテクチャの要件を満たしていることを確認します。 

* Visual Studio を使用してコードの構造、動作、および関係を視覚化することによって、既存のプログラム コードを容易に理解できるようになります。 

* アーキテクチャの依存関係を考慮し、必要でチームを教育します。  
  
* 開発プロセスの一部として、アプリケーション ライフサイクル全体においてさまざまな詳細レベルでモデルを作成できます。

参照してください[シナリオ: 視覚化を使用するツールとモデリング、設計を変更する](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)です。  
  
## <a name="to"></a>終了  
  
|||  
|-|-|  
|**コードの視覚化**:<br /><br /> -コード マップを作成して、コードの編成や関係を確認します。 アセンブリ、名前空間、クラス、メソッドなどの間の依存関係を視覚化します。<br />-コードからクラス ダイアグラムを作成することで、クラスの構造体と特定のプロジェクトのメンバーを参照します。<br />-コードを検証する依存関係図を作成し、コードと設計の間の競合を検出します。|-   [コードを視覚化します。](../modeling/visualize-code.md)<br />-   [クラスとその他の種類 (クラス デザイナー) の使用](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [ビデオ: Visual Studio 2015 コード マップを使ってコードが設計を理解します。](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [ビデオ: リアルタイムで、アーキテクチャの依存関係を検証します。](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**アーキテクチャを定義する**:<br /><br /> -定義し、依存関係図を作成し、コードのコンポーネント間の依存関係に対する制約を適用します。|-   [ビデオ: Visual Studio (チャネル 9) でアーキテクチャの依存関係を検証します。](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**要件とシステムを検証してデザインを目的としています。**<br /><br /> アーキテクチャを記述する依存関係図でコードの依存関係を検証し、設計と競合する変更を防止します。|-   [ビデオ: Visual Studio (チャネル 9) でアーキテクチャの依存関係を検証します。](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Team Foundation バージョン コントロールを使用してモデル、図、およびコード マップを共有する**:<br /><br /> -共有できるようにコード マップ、プロジェクト、および Team Foundation バージョン管理下にある deoendency 図を配置します。|Team Foundation のバージョン コントロール下でこれらの項目を使用するユーザーが複数いる場合は、バージョン管理の問題を回避するために、次のガイドラインを使用します。<br /><br /> -   [モデルと図のバージョン管理を管理します。](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**モデルと図をカスタマイズする**:<br /><br /> -ドメイン固有言語を作成します。|-   [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**T4 テンプレートを使用してテキストを生成する**:<br /><br /> -テキスト ベースのファイルを生成するのにテキスト ブロックとテンプレートの内部制御ロジックを使用します。<br /> T4 テンプレートのビルドには、MSBuild は Visual Studio に含まれる|-   [コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)|

各機能をサポートする Visual Studio のバージョンを参照してください[アーキテクチャとモデリング ツールのバージョンのサポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="types-of-models-and-their-uses"></a>モデルの種類とその用途  
  
|**モデルの種類と一般的な用途**|  
|-------------------------------------|  
|**コード マップ**<br /><br /> コード マップは、コードの編成や関係を理解するために役立ちます。<br /><br /> 一般的な用途:<br /><br /> -プログラムのコードを調べるため、その構造とその依存関係を理解できる、更新、およびのコストを見積もる方法で提案された変更します。<br /><br /> 参照トピック<br /><br /> -   [複数のソリューション間の依存関係を対応します。](../modeling/map-dependencies-across-your-solutions.md)<br />-   [コード マップを使ったアプリケーションのデバッグ](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [コード マップ アナライザーを使った潜在的な問題を検索します。](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**依存関係図**<br /><br /> 依存関係図では、レイヤーまたは明示的な依存関係があるブロックのセットとして、アプリケーションの構造を定義できます。 コード内の依存関係と依存関係図で説明された依存関係の競合を検出する検証を実行できます。<br /><br /> 一般的な用途:<br /><br /> ライフ サイクルを通じて多数の変更、アプリケーションの構造を安定します。<br />コードの変更をチェックインする前に意図しない依存関係の競合を検出します。<br /><br /> 参照トピック<br /><br /> -   [コードから依存関係図を作成します。](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)<br />-   [依存関係図をコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)|  
|**ドメイン固有言語 (DSL)**<br /><br /> DSL は、特定の目的のために設計する表記法です。 Visual Studio では、通常、グラフィックです。<br /><br /> 一般的な用途:<br /><br /> 生成またはアプリケーションの部分を構成します。 表記法およびツールを開発するには、作業が必要です。 これを行うと、UML のカスタマイズよりもドメインに適合する結果となることがあります。<br />-大規模プロジェクトまたは製品ラインの&1; つ以上のプロジェクトで使用することで、DSL およびそのツールを開発への投資が返されます。<br /><br /> 参照トピック<br /><br /> -   [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>情報の入手方法  
  
[Visual Studio の視覚化 >/documents/report1.rdl」のモデリング ツールのフォーラム](http://go.microsoft.com/fwlink/?LinkId=184720)  
  
## <a name="see-also"></a>関連項目  
 [新機能します。](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps およびアプリケーション ライフ サイクル管理](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)

