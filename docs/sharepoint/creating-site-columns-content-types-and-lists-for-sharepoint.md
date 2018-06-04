---
title: SharePoint のサイト列、コンテンツの種類、およびリストの作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8c1869f11d4202237d628ff3f15f73906822ec47
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692523"
---
# <a name="creating-site-columns-content-types-and-lists-for-sharepoint"></a>SharePoint のサイト列、コンテンツの種類、およびリストの作成
  Visual Studio には、さまざまな基本的な SharePoint アイテムの数などのプロジェクト項目テンプレートが用意されています*一覧*と*コンテンツの種類*、どちらのサイト内の列を組み込むことができます (または*フィールド*)。 コンテンツ タイプおよびリストの新しいデザイナーは、これらの項目をより簡単に作成を行います。  
  
## <a name="site-columns"></a>サイト内の列
 サイト内の列には、SharePoint プロジェクトに追加できる最も基本的な要素の 1 つがあります。 サイト内の列は、電話番号、コメント、またはメンバー リスト内の連絡先の都市名など、データの型を表します。  
  
 新しいサイト列プロジェクト項目テンプレートが容易作成元のサイト列よりも、以前のバージョンの Visual Studio です。 新しいサイト内の列を作成すると、その表示名、そのデータ型、およびサイト内の列を SharePoint に表示するグループなどの必要な情報が含まれるサイト内の列の Elements.xml ファイル内の XML を変更できます。 サイト内の列の詳細については、次を参照してください。[列の概要](http://go.microsoft.com/fwlink/?LinkId=224996)です。  
  
## <a name="content-types-and-lists"></a>コンテンツ タイプおよびリスト
 コンテンツの種類および一覧は、SharePoint で使用される要素の間で最も頻繁にです。  
  
 コンテンツの種類は、SharePoint リストまたはドキュメント ライブラリで、メタデータ、ワークフロー、および項目のカテゴリの動作を定義します。 たとえば、連絡先のリストまたはタスクの一覧で情報のコンテンツの種類を作成できます。 連絡先のコンテンツの種類名、電子メール、電話番号、およびアドレスなどの列があります。 サイト レベルで定義したコンテンツの種類は、サイト内の任意のリストまたはドキュメント ライブラリの依存しません。 別のリストまたは SharePoint サイト上のドキュメント ライブラリには、同じコンテンツの種類を使用できます。 同じリストまたはドキュメント ライブラリでいくつかのコンテンツの種類を使用することもできます。  
  
 一覧は、他のユーザーと共有できる SharePoint での情報のコレクションです。 リストは、データを含む列の行で構成されます。 リストの例に示します。 タスク一覧、連絡先リスト、およびお知らせリスト。  
  
 新しいコンテンツ タイプおよびリスト デザイナー[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]サイト コンテンツ タイプおよびリストの作成より簡単になりより直観的 Visual Studio の以前のバージョンで作成します。 UI を使用して、視覚的に、使い慣れた方法でコンテンツ タイプおよびリストを構築するためにできる、並べ替え、リスト内のデータをグループ化し、グループの見出しを使用することができます。 コンテンツの種類の詳細については、次を参照してください。[コンテンツ タイプ](http://go.microsoft.com/fwlink/?LinkId=224997)です。 リストの詳細については、次を参照してください。[リスト フォーム](http://go.microsoft.com/fwlink/?LinkId=224998)と[リスト ビュー](http://go.microsoft.com/fwlink/?LinkId=224999)です。  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[チュートリアル: SharePoint のサイト列、コンテンツ タイプ、およびリストの作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|カスタム コンテンツ タイプで使用されているサイト内の列を作成する方法を示します。 コンテンツの種類は、カスタム リストで使用されます。|  
  
## <a name="see-also"></a>関連項目
 [SharePoint 2010 の開発の概要します。](http://go.microsoft.com/fwlink/?LinkId=225000)  
  
 