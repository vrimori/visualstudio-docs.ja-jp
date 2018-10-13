---
title: Entity Data Model ツールでは、Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3a3d64aed3834d517cb916bfbbed47a263eb8619
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290473"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Visual Studio での entity Data Model ツール
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Entity Framework とは、.NET 開発者は、ドメイン固有オブジェクトを使用してリレーショナル データを操作できるオブジェクト リレーショナル マッピング テクノロジです。 開発者が通常記述しなければならないデータアクセス コードの多くが不要になります。 Entity Framework は、.NET アプリケーションの新しいテクノロジをモデリング推奨オブジェクト リレーショナル マッピング (ORM です)。  
  
 最新のリリース バージョンは、2016 年 3 月の時点で[Entity Framework 6](https://msdn.microsoft.com/data/ef)します。 [Entity Framework 7](https://docs.efproject.net/en/latest/)プレリリース版では、します。  
  
 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] ツールが構築するために設計された[!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)]アプリケーション。 詳細なドキュメント[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]ツールがここには: [Entity Framework](https://msdn.microsoft.com/data/jj590134)します。  
  
 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]ツールを作成できます、*概念モデル*既存のデータベースのグラフィカルに視覚化し、概念モデルを編集します。 また、グラフィカルな概念モデルを作成し、そのモデルをサポートするデータベースを生成することもできます。 いずれの場合も、基になるデータベースの変更時には、モデルを自動的に更新できるだけではなく、アプリケーションのオブジェクトレイヤー コードも自動生成できます。 データベースの生成とオブジェクトレイヤー コードの生成はカスタマイズ可能です。  
  
 Visual Studio 2015 での Entity Data Model ツールを構成する特定のツールを次に示します。  
  
-   使用することができます、 [!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]デザイナー** (**エンティティ デザイナー**) を視覚的に作成し、エンティティ、アソシエーション、マッピング、および継承関係を変更します。 **エンティティ デザイナー**も生成[!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)]または[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]オブジェクト レイヤー コード。  
  
-   使用することができます、  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]ウィザード**を既存のデータベースから概念モデルを生成し、データベース接続情報をアプリケーションに追加します。  
  
-   使用することができます、**データベース生成ウィザード**最初に概念モデルを作成し、モデルをサポートするデータベースを作成します。  
  
-   使用することができます、**モデルの更新ウィザード**を基になるデータベースの変更を行ったときに、概念モデル、ストレージ モデル、およびマッピングを更新します。  
  
    > [!NOTE]
    >  Visual Studio 2010 以降で[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]ツールがサポートされていない[!INCLUDE[ss2k](../includes/ss2k-md.md)]します。  
  
 ツールでは、生成または .edmx ファイルを変更します。 このファイルには、概念モデル、ストレージ モデル、およびそれらの間のマッピングについて説明する情報が含まれています。 詳細については、次を参照してください。 [EDMX](https://msdn.microsoft.com/data/jj650889.aspx)します。  
  
 Entity Framework Power Tools では、エンティティ データ モデルを使用するアプリケーションを構築するのに役立ちます。 ツールは、概念モデルを生成、既存のモデルの検証、概念モデルに基づくオブジェクト クラスが含まれているソース コード ファイルの生成、およびモデルを生成するビューを含むソース コード ファイルを生成することができます。 詳細については、次を参照してください。 [Pre-Generated マッピング ビュー](https://msdn.microsoft.com/data/dn469601.aspx)します。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|使用する方法について説明します[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]ツールが[!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)]アプリケーションを作成します。|  
|[Entity Data Model](http://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|上に構築されたアプリケーションによって使用されるデータを操作するための情報とリンクを示します[!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)]します。|  
|[(コンソール、WinForms、WPF など) の完全な .NET の概要](https://docs.efproject.net/en/latest/platforms/full-dotnet/getting-started.html)|Entity Framework 7 を使用する .NET デスクトップ アプリケーションを作成する方法のチュートリアルを提供します。|  
|[ASP.NET 5 アプリケーションを新しいデータベース](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Entity Framework 7 を使用して新しい ASP.NET 5 アプリケーションを作成する方法について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)

