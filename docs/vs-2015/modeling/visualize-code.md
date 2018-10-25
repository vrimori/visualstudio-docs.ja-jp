---
title: コードの視覚化 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 82ce653eda1ec074f050809845610fbc1ab1bc0c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833659"
---
# <a name="visualize-code"></a>コードの視覚化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio の視覚化ツールとモデリング ツールを使って、既存のコードを理解し、アプリケーションを記述することができます。 これにより、自分が実行した変更がコードにどのような影響を与えるかを理解し、その変更に起因する作業とリスクを評価することができます。 例:  
  
- コード内のリレーションシップを理解するには、そのリレーションシップをビジュアルにマッピングします。  
  
- システムのアーキテクチャを記述し、デザインとコードの一貫性を維持するには、レイヤー図を作成し、それらの図と照らし合わせてコードを検証します。  
  
- クラス構造を記述するには、クラス ダイアグラムを作成します。  
  
- システムのさまざまな面をモデル化して通信するには、Unified Modeling Language (UML) ダイアグラムを作成します。 たとえば、システムのコンポーネント、型、相互作用、およびプロセスをモデル化することができます。  
  
  またこれらのツールを使用すると、プロジェクトの関係者と簡単にやり取りすることができます。 たとえば、UML クラス ダイアグラムを使って、プロジェクトの関係者、ユーザー、およびチーム メンバーとシステムについて検討するための共通の用語集を作成することができます。  
  
  各機能をサポートする Visual Studio のバージョンを確認するには、「 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
## <a name="what-do-you-want-to-do"></a>実行する操作  
  
|||  
|-|-|  
|**コードとの関係を理解するには。**<br /><br /> 特定のコード間のリレーションシップをマッピングします。<br /><br /> ソリューション全体のコード内のリレーションシップの概要を確認します。<br /><br /> **注**: Visual Studio のこのリリースでは、 *依存関係グラフ* の代わりに、 *コード マップ*という用語を使用します。|-   [ソリューション間の依存関係をマップします。](../modeling/map-dependencies-across-your-solutions.md)<br />-   [アプリケーションをデバッグするコード マップの使用](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [コード マップ アナライザーを使った潜在的な問題を検索します。](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [デバッグ中に呼び出し履歴に対するメソッドをマップします。](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**クラス構造を理解するには。**<br /><br /> コードからクラス ダイアグラムを作成することで、プロジェクト内のクラスの構造を視覚化します。|[方法: プロジェクトにクラス ダイアグラムを追加する (クラス デザイナー)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**高レベルのシステム デザインについての説明し、そのデザインに対してコードの検証します。**<br /><br /> レイヤー図を作成することで、高レベルのシステム デザインと想定する依存関係を記述します。 このデザインと照らし合わせてコードを検証し、コード内の依存関係がデザインと一貫性があることを確認します。|-   [コードからレイヤー図を作成します。](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [レイヤー図: リファレンス](../modeling/layer-diagrams-reference.md)<br />-   [レイヤー図: ガイドライン](../modeling/layer-diagrams-guidelines.md)<br />-   [レイヤー図を使用したコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)|  
|**ユーザーの要件とアーキテクチャを通信します。**<br /><br /> 次の UML 図 (アクティビティ、コンポーネント、クラス、シーケンス、使用例) を描画することで、ソフトウェア システムのユーザー要求とアーキテクチャをモデル化します。|-   [アプリのモデルを作成します。](../modeling/create-models-for-your-app.md)<br />-   [ユーザー要件のモデリング](../modeling/model-user-requirements.md)<br />-   [アプリのアーキテクチャをモデル化します。](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="external-resources"></a>外部リソース  
  
|**カテゴリ**|**Links**|  
|------------------|---------------|  
|**フォーラム**|-   [Visual Studio の視覚化ツールとモデリング ツール](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio の視覚化ツールとモデリング SDK (DSL ツール)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**ブログ**|[Visual Studio ALM + Team Foundation Server のブログ](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技術記事とジャーナル**|[MSDN アーキテクチャ フォーラム](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>関連項目  
 [シナリオ: 視覚化を使用して、モデリング、設計を変更します。](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [分析およびアーキテクチャのモデリング](../modeling/analyze-and-model-your-architecture.md)   
 [アプリのモデルを作成します。](../modeling/create-models-for-your-app.md)   
 [ユーザー要件のモデリング](../modeling/model-user-requirements.md)   
 [アプリのアーキテクチャをモデル化します。](../modeling/model-your-app-s-architecture.md)   
 [開発プロセス内でのモデルの使用](../modeling/use-models-in-your-development-process.md)



