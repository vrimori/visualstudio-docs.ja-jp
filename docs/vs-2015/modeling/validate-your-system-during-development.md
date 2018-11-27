---
title: 開発中にシステムの検証 |Microsoft Docs
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
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 03cac924853f4348faabd773260a9512c2d82b6b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760973"
---
# <a name="validate-your-system-during-development"></a>開発時のシステムの検証
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio を使用すると、ソフトウェアがユーザーの要件とシステムのアーキテクチャに合致した状態を維持することができます。  
  
 これらの各機能をサポートする Visual Studio のバージョンを確認するには、「 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
## <a name="key-tasks"></a>主なタスク  
 ソフトウェアを検証するには、次のタスクを使用します。  
  
|**タスク**|**関連するトピック**|  
|---------------|---------------------------|  
|**モデルが一貫して確認します。**<br /><br /> プロジェクトでのモデルの使用方法および解釈方法によっては、いくつかの要素の組み合わせを許可しないようにすると効果的です。 たとえば、必ず [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] に準拠した名前を使用するように UML クラスを制限することができます。 そのような制約は [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の拡張機能で定義できます。|-   [UML モデルを検証します。](../modeling/validate-your-uml-model.md)<br />-   [UML モデルの検証制約を定義します。](../modeling/define-validation-constraints-for-uml-models.md)|  
|**ソフトウェアがユーザーの要件を満たしているか確認する**:<br /><br /> システムとそのコンポーネントのテストを編成する際に、要件モデルとアーキテクチャ モデルを使用できます。 こうすることで、ユーザーやその他の利害関係者にとって重要な要求をテストしやすくなり、要求が変更された場合にすばやくテストを更新することができます。|-   [モデルからテストを開発します。](../modeling/develop-tests-from-a-model.md)|  
|**ソフトウェアが、意図されたシステム設計に合致した状態を保っているか確認する:**<br /><br /> レイヤー図は、アプリケーションのコンポーネント間の、意図された依存関係を表します。 開発中に、コード内の実際の依存関係が、意図された設計に準拠しているか検証できます。|-   [コードからレイヤー図を作成します。](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [レイヤー図を使用したコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>外部リソース  
  
|**カテゴリ**|**リンク**|  
|------------------|---------------|  
|**ビデオ**|![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug 7: コードの理解と Visual Studio 2010 のシステムの設計](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: レイヤー図を使用してアプリケーションの設計](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I Series: レイヤー図を使用してコードを検証する方法](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**フォーラム**|-   [Visual Studio の視覚化ツールとモデリング ツール](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio の視覚化ツールとモデリング SDK (DSL ツール)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**ブログ**|-   [Visual Studio ALM + Team Foundation Server のブログ](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技術記事とジャーナル**|[MSDN アーキテクチャ センター](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>関連項目  
 [アプリケーションのテスト](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [UML モデルと図を拡張します。](../modeling/extend-uml-models-and-diagrams.md)   
 [ユーザー要件のモデリング](../modeling/model-user-requirements.md)   
 [アーキテクチャの分析およびモデリング](../modeling/analyze-and-model-your-architecture.md)



