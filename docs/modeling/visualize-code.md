---
title: "コードの視覚化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 47
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: aa7e0e7e9bbd4d4a3f8a1b2fa82f1ce7a6ba3e53
ms.lasthandoff: 02/22/2017

---
# <a name="visualize-code"></a>コードの視覚化
Visual Studio の視覚化ツールとモデリング ツールを使って、既存のコードを理解し、アプリケーションを記述することができます。 これにより、自分が実行した変更がコードにどのような影響を与えるかを理解し、その変更に起因する作業とリスクを評価することができます。 例:  
  
-   コード内のリレーションシップを理解するには、そのリレーションシップをビジュアルにマッピングします。  
  
-   システムのアーキテクチャについて説明し、コードの設計と一貫性を維持、依存関係図を作成し、これらの図と照らし合わせてコードを検証します。  
  
-   クラス構造を記述するには、クラス ダイアグラムを作成します。  
  
 またこれらのツールを使用すると、プロジェクトの関係者と簡単にやり取りすることができます。 
  
 各機能をサポートする Visual Studio のバージョンを参照してください[アーキテクチャとモデリング ツールのバージョンのサポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="what-do-you-want-to-do"></a>実行する操作  
  
|||  
|-|-|  
|**コードとの関係を理解しています。**<br /><br /> 特定のコード間のリレーションシップをマッピングします。<br /><br /> ソリューション全体のコード内のリレーションシップの概要を確認します。<br /><br /> **注**: Visual Studio のこのリリースでは、 *依存関係グラフ* の代わりに、 *コード マップ*という用語を使用します。|-   [複数のソリューション間の依存関係を対応します。](../modeling/map-dependencies-across-your-solutions.md)<br />-   [コード マップを使ったアプリケーションのデバッグ](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [コード マップ アナライザーを使った潜在的な問題を検索します。](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [デバッグ中に呼び出し履歴に対するメソッドをマップします。](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**クラス構造を理解しています。**<br /><br /> コードからクラス ダイアグラムを作成することで、プロジェクト内のクラスの構造を視覚化します。|[方法: プロジェクトにクラス ダイアグラムを追加する (クラス デザイナー)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**高レベルのシステムの設計を記述し、この設計に照らし合わせてコードを検証します。**<br /><br /> 依存関係図を作成し、高レベルのシステム デザインと想定する依存関係を説明します。 このデザインと照らし合わせてコードを検証し、コード内の依存関係がデザインと一貫性があることを確認します。|-   [コードから依存関係図を作成します。](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)<br />-   [依存関係図: ガイドライン](../modeling/layer-diagrams-guidelines.md)<br />-   [依存関係図をコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>外部リソース  
  
|**カテゴリ**|**リンク**|  
|------------------|---------------|  
|**フォーラム**|-   [Visual Studio の視覚化 >/documents/report1.rdl」のモデリング ツール](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio の視覚化 >/reportbuilder/reportbuilder_3_0_0_0.application Modeling SDK (DSL ツール)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**ブログ**|[Visual Studio ALM と Team Foundation Server ブログ](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技術文書およびジャーナル**|[MSDN アーキテクチャ フォーラム](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>関連項目  
 [シナリオ: 視覚化を使用するツールとモデリング、設計を変更します。](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [分析ツールとアーキテクチャのモデリング](../modeling/analyze-and-model-your-architecture.md)   
 [モデルのアプリのアーキテクチャ](../modeling/model-your-app-s-architecture.md)   
 [開発プロセス内でのモデルの使用](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

