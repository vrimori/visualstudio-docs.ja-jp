---
title: "開発中にシステムを検証する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 37
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
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: d35e357a62c467d20f5a97a469ac5f89324b4391
ms.lasthandoff: 02/22/2017

---
# <a name="validate-your-system-during-development"></a>開発時のシステムの検証
Visual Studio を使用すると、ソフトウェアがユーザーの要件とシステムのアーキテクチャに合致した状態を維持することができます。  
  
 これらの各機能をサポートする Visual Studio のバージョンを確認するを参照してください。[アーキテクチャとモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)します。  
  
## <a name="key-tasks"></a>主なタスク  
 ソフトウェアを検証するには、次のタスクを使用します。  
  
|**タスク**|**関連するトピック**|  
|---------------|---------------------------|  
|**ソフトウェアがユーザーの要件を満たしているか確認する**:<br /><br /> システムとそのコンポーネントのテストを編成する際に、要件モデルとアーキテクチャ モデルを使用できます。 こうすることで、ユーザーやその他の利害関係者にとって重要な要求をテストしやすくなり、要求が変更された場合にすばやくテストを更新することができます。|-   [モデルからのテストを作成します。](../modeling/develop-tests-from-a-model.md)|  
|**システムの設計と整合性、ソフトウェアがあることを確認します。**<br /><br /> 依存関係の図は、アプリケーションのコンポーネント間で目的の依存関係を記述します。 開発中に、コード内の実際の依存関係が、意図された設計に準拠しているか検証できます。|-   [コードから依存関係図を作成します。](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [依存関係図をコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>外部リソース  
  
|**カテゴリ**|**リンク**|  
|------------------|---------------|  
|**ビデオ**|![ビデオへのリンク](~/docs/data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug 7: コードの理解と Visual Studio 2010 のシステムの設計](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![ビデオへのリンク](~/docs/data-tools/media/playvideo.gif "PlayVideo") [Channel 9: 依存関係図を使用してアプリケーションの設計](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![ビデオへのリンク](~/docs/data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I Series: 依存関係図を使用してコードを検証する方法](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**フォーラム**|-   [Visual Studio の視覚化 >/documents/report1.rdl」のモデリング ツール](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio の視覚化 >/reportbuilder/reportbuilder_3_0_0_0.application Modeling SDK (DSL ツール)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**ブログ**|-   [Visual Studio ALM と Team Foundation Server ブログ](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技術文書およびジャーナル**|[MSDN アーキテクチャ センター](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>関連項目  
 [アプリケーションのテスト](https://www.visualstudio.com/en-gb/docs/test/overview)   
 [モデルのユーザーの要件](../modeling/model-user-requirements.md)   
 [アーキテクチャの分析およびモデリング](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

