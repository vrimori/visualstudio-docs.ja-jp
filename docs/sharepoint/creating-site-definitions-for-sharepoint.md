---
title: "SharePoint のサイト定義を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 98be671e456c75c4be79994c84bf1ed6ae5114de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-site-definitions-for-sharepoint"></a>SharePoint のサイト定義の作成
  SharePoint サイト定義プロジェクト[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を作成することができます、*サイト定義*、新しい SharePoint サイトの基礎として使用します。 だけでなく、これらの定義は、SharePoint サイトの既定のコンテンツやも機能の動作と外観を決定します。 定義では、構成済みのリスト、コンテンツの種類、イベント レシーバー、画像、およびその他のアイテムを配置できます。 SharePoint には、たとえば、ブログなどの一部のサイト定義が含まれます。 ブログ サイト定義に基づくサイトを作成するときに、サイトには、リスト、Web パーツ、およびブログ サイトが必要なその他のアイテムが含まれています。  
  
 サイト定義の詳細については、次を参照してください。[サイト テンプレートと定義](http://go.microsoft.com/fwlink/?LinkId=179134)です。  
  
## <a name="site-definition-projects"></a>サイト定義プロジェクト  
 サイト定義プロジェクト[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint サイトに必要な基本的なファイルのみの提供です。 既定の機能は提供されません。 ファイルとする機能を提供するコンテンツを追加する必要があります。 作成し、必要なファイルを追加するサイトを手動で構築できます。  
  
## <a name="feature-stapling"></a>ホチキス止め機能  
 サイト定義を作成する利点の 1 つ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]は自動的に使用する*ホチキス止め機能*します。 ホチキス止めの機能は、サイト定義は、サイト定義自体でその機能を埋め込む代わりに、機能をアタッチします。 これを行うには、元のサイト定義を変更することがなく、サイト定義を使用して作成されたすべてのサイトに機能を追加することができます。 詳細については、次を参照してください。[ホチキス止め機能](http://go.microsoft.com/fwlink/?LinkID=119283)します。  
  
## <a name="site-definition-project-components"></a>サイト定義プロジェクト コンポーネント  
 次の既定のファイルを追加サイト定義ソリューションを作成するときにその**SiteDefinition**ノード。  
  
|ファイル名|説明|  
|---------------|-----------------|  
|default.aspx|新しい SharePoint サイトの既定の ASPX ホーム ページです。|  
|Onet.xml|新しいサイトの構成のコンポーネント、サイト定義のテンプレートと既定の動作を指定します。 これらの設定は、コンテンツの種類、有効な既定のリスト ビューで、ドキュメント テンプレート ファイルなどの属性を含めるし、Web サイトに含まれているパーツできます。 既定では、`Modules`セクションには、SharePoint サイトとその構成に追加するファイルが一覧表示します。|  
|webtemp_*SiteDefinitionName*.xml|表示されるサイト定義構成を指定します、**テンプレートの選択**のセクションで、**新しい SharePoint サイト**ページ。|  
  
 既定では、すべてのサイト定義が格納されている、*ドライブ:*\program files \microsoft shared \web Server Extensions\14\TEMPLATE\SiteTemplates フォルダーです。 各サイトの定義は、それぞれのサブフォルダーが。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[チュートリアル: 基本サイト定義プロジェクトの作成](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|基本的なサイト定義プロジェクトの作成を追って[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。|  
|[方法: カスタムのサイト定義と構成の作成](http://go.microsoft.com/fwlink/?LinkId=183309)|既存のサイト定義をコピーして、コピーを変更し、SharePoint でカスタムのサイト定義を作成する方法について説明します。|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|使用可能なサイト定義を指定する元のファイルについて説明します、**テンプレートの選択**のセクションで、**新しい SharePoint サイト**ページ。|  
|[SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)|グローバルに使用できる、SharePoint ソリューションを準備する方法について説明します。|  
|[SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)|ユーザーを変更できる SharePoint ページの部分を作成する方法について説明します。|  
|[Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|アプリケーション ページと Web パーツで実行される再利用可能なコントロールを作成する方法について説明します。|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|プロジェクトで Web ページを開くときに表示されるデザイナーを使用する方法について説明します。|  
|[ASP.NET Web Pages の概要](http://go.microsoft.com/fwlink/?LinkId=178726)|構造に関する全般情報を提供[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]Web ページ、ページの処理方法[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]、およびどのように[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]ページは XHTML 標準に準拠するマークアップを表示します。|  
|[ASP.NET Web ページの構文](http://go.microsoft.com/fwlink/?LinkId=178727)|ASP.NET ページを構成するマークアップ要素について説明します。|  
|[ASP.NET Web Pages のプログラミング](http://go.microsoft.com/fwlink/?LinkId=178728)|内のイベント ハンドラーを作成する方法に関する情報を提供[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]ページとクライアント スクリプトを操作する方法です。|  
|[Windows SharePoint Services でのプログラミング](http://go.microsoft.com/fwlink/?LinkId=178729)|提供されているマネージ オブジェクト モデルを使用する方法について説明[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]です。|  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  