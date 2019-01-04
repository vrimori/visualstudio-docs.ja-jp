---
title: For SharePoint のサイト定義の作成 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66e3566b7bfabb7ec2049632937beaa697246403
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868327"
---
# <a name="create-site-definitions-for-sharepoint"></a>SharePoint のサイト定義を作成します。
  SharePoint サイト定義プロジェクト[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を作成することができます、*サイト定義*、新しい SharePoint サイトの基盤として機能します。 だけでなく、これらの定義は、SharePoint サイトも既定の内容と機能の動作と外観を決定します。 定義では、事前構成済みのリスト、コンテンツの種類、イベント レシーバー、イメージ、およびその他のアイテムを配置できます。 SharePoint には、たとえば、ブログなどのいくつかのサイト定義が含まれます。 ブログ サイト定義に基づいてサイトを作成するときに、サイトには、リスト、Web パーツ、およびブログ サイトを必要とするその他の項目が含まれています。  
  
 サイト定義の詳細については、次を参照してください。[サイト テンプレートと定義](http://go.microsoft.com/fwlink/?LinkId=179134)します。  
  
## <a name="site-definition-projects"></a>サイト定義プロジェクト
 サイト定義プロジェクトで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint サイトに必要な基本的なファイルのみを提供する; 既定の機能は提供されません。 ファイルとする機能を提供するコンテンツを追加する必要があります。 作成に必要なファイルを追加して、手動でサイトを構築できます。  
  
## <a name="feature-stapling"></a>ホチキス止め機能
 サイト定義の作成の利点の 1 つ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]が自動的に使用する*ホチキス止め機能*します。 ホチキス止めの機能は、機能をサイト定義自体でその機能を埋め込む代わりのサイト定義にアタッチします。 これを行うには、元のサイト定義を変更することがなく、サイト定義を使用して作成されたすべてのサイトに機能を追加することができます。 詳細については、次を参照してください。[ホチキス止め機能](http://go.microsoft.com/fwlink/?LinkID=119283)します。  
  
## <a name="site-definition-project-components"></a>サイト定義プロジェクトのコンポーネント
 次の既定のファイルを追加サイト定義ソリューションを作成するときにその**SiteDefinition**ノード。  
  
|ファイル名|説明|  
|---------------|-----------------|  
|*Default.aspx*|新しい SharePoint サイトの既定の ASPX ホーム ページ。|  
|*Onet.xml*|新しいサイトの構成のコンポーネント、サイト定義のテンプレート、および既定の動作を指定します。 これらの設定は、コンテンツの種類を有効になっている既定のリスト ビューで、ドキュメント テンプレートのファイルなどの属性を含めるし、Web サイトに含まれているパーツ。 既定で、`Modules`セクションには、SharePoint サイトとその構成に追加するファイルが一覧表示されます。|  
|*webtemp_\<SiteDefinitionName > .xml*|表示されるサイト定義構成を指定します、**テンプレートの選択**のセクション、**新しい SharePoint サイト**ページ。|  
  
 既定では、すべてのサイト定義が格納されている、 *\<ドライブ: > \Program Files\Common \microsoft shared \web Server Extensions\14\TEMPLATE\SiteTemplates*フォルダー。 各サイトの定義が、それぞれのサブフォルダーです。  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[チュートリアル: 基本的なサイト定義プロジェクトを作成します。](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|基本的なサイト定義プロジェクトの作成を追って[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。|  
|[方法: カスタム サイト定義と構成を作成します。](http://go.microsoft.com/fwlink/?LinkId=183309)|既存のサイト定義をコピーして、コピーを変更し、SharePoint でカスタム サイト定義を作成する方法について説明します。|  
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|使用可能なサイト定義を指定する元のファイルについて説明します、**テンプレートの選択**のセクション、**新しい SharePoint サイト**ページ。|  
|[SharePoint ソリューションをローカライズします。](../sharepoint/localizing-sharepoint-solutions.md)|グローバルに使用できる、SharePoint ソリューションを準備する方法について説明します。|  
|[For SharePoint の web パーツを作成します。](../sharepoint/creating-web-parts-for-sharepoint.md)|ユーザーが変更できる SharePoint ページの部分を作成する方法について説明します。|  
|[Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成します。](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|アプリケーション ページと Web パーツで実行される再利用可能なコントロールを作成する方法について説明します。|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|プロジェクトで Web ページを開くときに表示されるデザイナーを使用する方法について説明します。|  
|[ASP.NET Web ページの概要](http://go.microsoft.com/fwlink/?LinkId=178726)|構造についての一般的な情報を提供します[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]Web ページ、ページの処理方法[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]、どのように[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]ページが XHTML 標準に準拠しているマークアップを表示します。|  
|[ASP.NET Web ページの構文](http://go.microsoft.com/fwlink/?LinkId=178727)|ASP.NET ページを構成するマークアップ要素について説明します。|  
|[ASP.NET Web Pages のプログラミング](http://go.microsoft.com/fwlink/?LinkId=178728)|内のイベント ハンドラーを作成する方法についての情報を提供します[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]ページとクライアント スクリプトを操作する方法。|  
|[Windows SharePoint Services でのプログラミング](http://go.microsoft.com/fwlink/?LinkId=178729)|提供されているマネージ オブジェクト モデルを使用する方法について説明します[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]します。|  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
