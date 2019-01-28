---
title: For SharePoint のサイト列、コンテンツの種類、およびリストの作成 |Microsoft Docs
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8ec1bc999025128c0dd68281dfc53e3f6353ae6b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875551"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>For SharePoint のサイト列、コンテンツの種類、およびリストを作成します。
  Visual Studio には、さまざまな基本的な SharePoint アイテムの数などのプロジェクト項目テンプレートが用意されています*一覧*と*コンテンツの種類*、どちらのサイト内の列を組み込むことができます (または*フィールド*)。 コンテンツ タイプおよびリスト用の新しいデザイナーは、これらの項目をより簡単に作成します。  
  
## <a name="site-columns"></a>サイト内の列
 サイト内の列には、SharePoint プロジェクトに追加できる最も基本的な要素の 1 つがあります。 サイト内の列は、電話番号、コメント、または連絡先のリストで連絡先の都市名などのデータの種類を表します。  
  
 新しいサイト列プロジェクト項目テンプレートでは、Visual Studio の以前のバージョンよりも簡単にサイト列を作成できるように。 新しいサイト内の列を作成した後で、サイト内の列の XML を変更できます*Elements.xml*ファイルの表示名、そのデータ型では、サイト列を表示するグループなど、必要な情報を含めるSharePoint。 サイト内の列の詳細については、次を参照してください。[列の概要](http://go.microsoft.com/fwlink/?LinkId=224996)します。  
  
## <a name="content-types-and-lists"></a>コンテンツ タイプおよびリスト
 コンテンツ タイプおよびリストのうち、最も頻繁に SharePoint で使用される要素。  
  
 コンテンツの種類は、SharePoint リストまたはドキュメント ライブラリで、メタデータ、ワークフロー、および項目のカテゴリの動作を定義します。 たとえば、連絡先リストまたはタスクの一覧で情報のコンテンツ タイプを作成できます。 連絡先のコンテンツの種類には、名前、電子メール、電話番号、およびアドレスなどの列が含まれます。 サイト レベルで定義したコンテンツの種類は、サイト内の任意のリストやドキュメント ライブラリの依存しません。 異なるリストまたは SharePoint サイト上のドキュメント ライブラリでは、同じコンテンツ型を使用できます。 同じリストまたはドキュメント ライブラリにいくつかのコンテンツ タイプを使用することもできます。  
  
 一覧は、他のユーザーと共有できる SharePoint で情報のコレクションです。 リストは、データを含む列の行で構成されます。 リストの例を示します。 タスク一覧、連絡先リスト、およびお知らせリスト。  
  
 新しいコンテンツ タイプおよびリスト デザイナー[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]サイト コンテンツ タイプおよびリストの作成より簡単でよりもより直感的な Visual Studio の以前のバージョンで作成します。 UI では、視覚的に、使い慣れた方法でコンテンツ タイプおよびリストを構築することができ、並べ替え、リスト内のデータをグループ化し、グループの見出しを使用することができます。 コンテンツの種類の詳細については、次を参照してください。[コンテンツ タイプの](http://go.microsoft.com/fwlink/?LinkId=224997)します。 リストの詳細については、次を参照してください。[リスト フォーム](http://go.microsoft.com/fwlink/?LinkId=224998)と[リスト ビュー](http://go.microsoft.com/fwlink/?LinkId=224999)します。  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[チュートリアル: For SharePoint のサイト列、コンテンツの種類、および一覧を作成します。](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|カスタム コンテンツ タイプで使用されるサイト内の列を作成する方法を示します。 コンテンツの種類は、カスタム リストで使用されます。|  
  
## <a name="see-also"></a>関連項目
 [SharePoint 2010 で開発を開始します。](http://go.microsoft.com/fwlink/?LinkId=225000)  
