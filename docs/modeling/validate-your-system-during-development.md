---
title: 開発時のシステムの検証
ms.date: 11/04/2016
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d4ebc815f474f1b8a1c59c9736f9014ba02e523
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="validate-your-system-during-development"></a>開発時のシステムの検証
Visual Studio を使用すると、ソフトウェアがユーザーの要件とシステムのアーキテクチャに合致した状態を維持することができます。

 これらの各機能をサポートする Visual Studio のバージョンを確認するには、「 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。

## <a name="key-tasks"></a>主なタスク
 ソフトウェアを検証するには、次のタスクを使用します。

|**タスク**|**関連するトピック**|
|---------------|---------------------------|
|**ソフトウェアがユーザーの要件を満たしているか確認する**:<br /><br /> システムとそのコンポーネントのテストを編成する際に、要件モデルとアーキテクチャ モデルを使用できます。 こうすることで、ユーザーやその他の利害関係者にとって重要な要求をテストしやすくなり、要求が変更された場合にすばやくテストを更新することができます。|-   [モデルからのテストを開発します。](../modeling/develop-tests-from-a-model.md)|
|**ソフトウェアが、意図されたシステム設計に合致した状態を保っているか確認する:**<br /><br /> 依存関係の図は、アプリケーションのコンポーネント間で目的の依存関係を記述します。 開発中に、コード内の実際の依存関係が、意図された設計に準拠しているか検証できます。|-   [コードから依存関係のダイアグラムを作成します。](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [依存関係のダイアグラムのコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>外部リソース

|**カテゴリ**|**リンク**|
|------------------|---------------|
|**ビデオ**|![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug 7: コードの理解と Visual Studio 2010 のシステムの設計](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: 依存関係ダイアグラムを使用してアプリケーションの設計](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I シリーズ: 依存関係図を使用してコードを検証する方法](http://go.microsoft.com/fwlink/?LinkID=214405)|
|**フォーラム**|-   [Visual Studio の視覚化ツールとモデリング ツール](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio の視覚化ツールとモデリング SDK (DSL ツール)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**ブログ**|-   [Visual Studio ALM + Team Foundation Server のブログ](http://go.microsoft.com/fwlink/?LinkID=201340)|
|**技術記事とジャーナル**|[MSDN アーキテクチャ センター](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>関連項目

- [アプリケーションのテスト](https://www.visualstudio.com/en-gb/docs/test/overview)
- [ユーザー要件のモデリング](../modeling/model-user-requirements.md)
- [アーキテクチャの分析およびモデリング](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
