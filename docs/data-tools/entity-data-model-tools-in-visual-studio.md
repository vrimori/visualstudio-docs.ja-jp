---
title: Visual Studio での entity Framework ツール
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 679c91014966167c64296638d9d0a9b2d302d345
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284043"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Visual Studio での entity Framework ツール
Entity Framework とは、.NET 開発者は、ドメイン固有オブジェクトを使用してリレーショナル データを操作できるオブジェクト リレーショナル マッピング テクノロジです。 開発者が通常記述しなければならないデータアクセス コードの多くが不要になります。 Entity Framework は、.NET アプリケーションの新しいテクノロジをモデリング推奨オブジェクト リレーショナル マッピング (ORM です)。

Entity Framework ツールは、Entity Framework (EF) アプリケーションを構築するために設計されています。 Entity Framework の完全なドキュメントについてはこちら: [EF Core と EF 6](/ef/)します。

Entity Framework のツールで作成できます、*概念モデル*既存のデータベースのグラフィカルに視覚化し、概念モデルを編集します。 また、グラフィカルな概念モデルを作成し、そのモデルをサポートするデータベースを生成することもできます。 いずれの場合も、基になるデータベースの変更時には、モデルを自動的に更新できるだけではなく、アプリケーションのオブジェクトレイヤー コードも自動生成できます。 データベースの生成とオブジェクトレイヤー コードの生成はカスタマイズ可能です。

一部として、Entity Framework ツールがインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード。 個々 のコンポーネントとしてインストールすることも、 **Sdk、ライブラリ、およびフレームワーク**カテゴリ。

Visual Studio で Entity Framework のツールを構成する特定のツールを次に示します。

-   使用することができます、 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]デザイナー** (**エンティティ デザイナー**) を視覚的に作成し、エンティティ、アソシエーション、マッピング、および継承関係を変更します。 **エンティティ デザイナー**も生成[!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)]または[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]オブジェクト レイヤー コード。

-   使用することができます、  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]ウィザード**を既存のデータベースから概念モデルを生成し、データベース接続情報をアプリケーションに追加します。

-   使用することができます、**データベース生成ウィザード**最初に概念モデルを作成し、モデルをサポートするデータベースを作成します。

-   使用することができます、**モデルの更新ウィザード**を基になるデータベースの変更を行ったときに、概念モデル、ストレージ モデル、およびマッピングを更新します。

    > [!NOTE]
    >  Visual Studio 2010 以降では、Entity Framework ツールがサポートしない[!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)]します。

ツールを生成または変更、 *.edmx*ファイル。 これは、 *.edmx*ファイルには、概念モデル、ストレージ モデル、およびそれらの間のマッピングについて説明する情報が含まれています。 詳細については、次を参照してください。 [EDMX](https://docs.microsoft.com/ef/ef6/)します。

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4)エンティティ データ モデルを使用するアプリケーションを構築できます。 パワー ツールは、概念モデルを生成、既存のモデルの検証、概念モデルに基づくオブジェクト クラスが含まれているソース コード ファイルの生成、およびモデルを生成するビューを含むソース コード ファイルを生成することができます。 詳細については、次を参照してください。 [Pre-Generated マッピング ビュー](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views)します。

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|使用する方法について説明します[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]ツールが[!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]アプリケーションを作成します。|
|[Entity Data Model](/dotnet/framework/data/adonet/entity-data-model)|上に構築されたアプリケーションによって使用されるデータを操作するための情報とリンクを示します[!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]します。|
|[Entity Framework (EF) のドキュメント)](https://docs.microsoft.com/ef/ef6/get-started)|ビデオ、チュートリアル、および Entity Framework を最大限に活用するための高度なドキュメントのインデックスを提供します。|
|[ASP.NET 5 アプリケーションを新しいデータベース](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Entity Framework 7 を使用して新しい ASP.NET 5 アプリケーションを作成する方法について説明します。|

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)