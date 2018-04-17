---
title: Visual Studio での entity Framework ツール |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c9335e5d5bba077a2fd517e80398fa452718fed3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="entity-framework-tools-in-visual-studio"></a>Visual Studio での entity Framework ツール
Entity Framework は、.NET 開発者は、ドメイン固有のオブジェクトを使用してリレーショナル データを操作するオブジェクト リレーショナル マッピング テクノロジです。 開発者が通常記述しなければならないデータアクセス コードの多くが不要になります。 Entity Framework は、新しい .NET アプリケーションのテクノロジをモデリング推奨オブジェクト リレーショナル マッピング (ORM) です。  
  
Entity Framework ツールは、Entity Framework (EF) アプリケーションを構築するために設計されています。 ここでは、Entity Framework に関する完全なドキュメント: [EF コアと EF 6](/ef/)です。  
  
Entity Framework ツールを作成できます、*概念モデル*既存のデータベースし視覚的に視覚化し、概念モデルを編集します。 また、グラフィカルな概念モデルを作成し、そのモデルをサポートするデータベースを生成することもできます。 いずれの場合も、基になるデータベースの変更時には、モデルを自動的に更新できるだけではなく、アプリケーションのオブジェクトレイヤー コードも自動生成できます。 データベースの生成とオブジェクトレイヤー コードの生成はカスタマイズ可能です。  
  
一部として、Entity Framework ツールがインストールされている、**データ ストレージと処理**Visual Studio インストーラーでのワークロードです。 下にある個々 のコンポーネントとしてインストールすることも、 **Sdk、ライブラリ、およびフレームワーク**カテゴリ。  
 
Visual Studio での Entity Framework ツールを構成する特定のツールを次に示します。  
  
-   使用することができます、 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]デザイナー** (**エンティティ デザイナー**) を視覚的に作成およびエンティティ、アソシエーション、マッピング、および継承関係を変更します。 **エンティティ デザイナー**も生成[!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)]または[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]オブジェクトレイヤー コード。  
  
-   使用することができます、  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]ウィザード**を既存のデータベースからの概念モデルを生成し、データベースの接続情報をアプリケーションに追加します。  
  
-   使用することができます、**データベースの作成ウィザード**最初概念モデルを作成し、モデルをサポートするデータベースを作成します。  
  
-   使用することができます、**モデルの更新ウィザード**を基になるデータベースに変更が加えられたときに、概念モデル、ストレージ モデル、およびマッピングを更新します。  
  
    > [!NOTE]
    >  Visual Studio 2010 以降、Entity Framework ツールがサポートしない[!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)]です。  
  
ツールは、生成または .edmx ファイルを変更します。 .Edmx ファイルには、概念モデル、ストレージ モデル、およびそれらの間のマッピングを記述する情報が含まれています。 詳細については、次を参照してください。 [EDMX](https://msdn.microsoft.com/data/jj650889.aspx)です。  
  
[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4)エンティティ データ モデルを使用するアプリケーションの構築を支援します。 パワー ツールは、概念モデルを生成、既存のモデルを検証、概念モデルに基づくオブジェクト クラスを含むソース コード ファイルを生成、およびモデルを生成するビューを含むソース コード ファイルを生成することができます。 詳細については、次を参照してください。 [Pre-Generated マッピング ビュー](https://msdn.microsoft.com/data/dn469601.aspx)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|使用する方法について説明します[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]ツールを[!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]提供するアプリケーションを作成します。|  
|[Entity Data Model](/dotnet/framework/data/adonet/entity-data-model)|構築されたアプリケーションによって使用されるデータを操作するための情報とリンクを示します[!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]です。|  
|[Entity Framework (EF) ドキュメント)](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|ビデオ、チュートリアル、および Entity Framework を最大限に活用するための高度なドキュメントのインデックスを提供します。|  
|[ASP.NET 5 アプリケーションを新しいデータベース](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Entity Framework 7 を使用して、新しい ASP.NET 5 アプリケーションを作成する方法について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)