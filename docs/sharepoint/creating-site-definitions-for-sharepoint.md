---
title: "SharePoint のサイト定義の作成"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発、サイト定義"
  - "サイト定義 [Visual Studio での SharePoint 開発]"
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# SharePoint のサイト定義の作成
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の SharePoint サイト定義プロジェクトを使用すると、新しい SharePoint サイトの基盤として機能する*サイト定義*を作成できます。  これらの定義は、SharePoint サイトの外観と動作だけでなく、その既定の内容と機能も決定します。  定義には、構成済みのリスト、コンテンツ タイプ、イベント レシーバー、イメージ、およびそのほかの項目を配置できます。  SharePoint には、ブログなどのサイト定義がいくつか含まれています。たとえば、  ブログ サイト定義に基づいて作成したサイトには、リストや Web パーツなど、ブログ サイトに必要な項目が含まれます。  
  
 サイト定義の詳細については、参照します [Site Templates と定義](http://go.microsoft.com/fwlink/?LinkId=179134)。  
  
## サイト定義プロジェクト  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のサイト定義プロジェクトは、SharePoint サイトに必要な基本的なファイルのみを提供します。既定の機能は提供しません。  目的の機能を提供するためのファイルとコンテンツを追加する必要があります。  サイトは、必要なファイルを作成して追加することにより、手動で構築できます。  
  
## ホチキス止め機能  
 サイト定義を [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で作成することの利点の 1 つは、サイト定義が自動的に*ホチキス止め機能*を使用することです。  ホチキス止め機能は、フィーチャーの機能をサイト定義そのものに埋め込むのではなく、フィーチャーをサイト定義にアタッチします。  これにより、そのサイト定義を使って作成されたすべてのサイトに同じフィーチャーを追加できます。元のサイト定義を変更する必要はありません。  詳細については、参照します [ホチキス止め機能](http://go.microsoft.com/fwlink/?LinkID=119283)。  
  
## サイト定義プロジェクトの構成要素  
 サイト定義ソリューションを作成すると、既定のファイルとして次のファイルが **SiteDefinition** ノードに追加されます。  
  
|ファイル名|説明|  
|-----------|--------|  
|default.aspx|新しい SharePoint サイトに使用される既定の ASPX ホーム ページです。|  
|onet.xml|新しいサイトの構成、サイト定義テンプレートのコンポーネント、および既定の動作を指定します。  これらの設定には、有効になっているコンテンツ タイプなどの属性、既定のリスト ビュー、ドキュメント テンプレート ファイル、サイトに含まれる Web パーツなどがあります。  既定では、`Modules` セクションで、SharePoint サイトに追加されるファイルとその構成方法が指定されています。|  
|webtemp\_*SiteDefinitionName*.xml|**\[新しい SharePoint サイト\]** ページの **\[テンプレートの選択\]** セクションに表示されるサイト定義構成を指定します。|  
  
 既定では *drive:*の\\Program の Files\\Common Files\\Microsoft Shared\\Web サーバー Extensions\\14\\TEMPLATE\\SiteTemplates フォルダーで、すべてのサイト定義格納されます。  それぞれのサイト定義には、独自のサブフォルダーがあります。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[チュートリアル: 基本サイト定義プロジェクトの作成](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で基本的なサイト定義プロジェクトを作成する方法について手順を追って説明します。|  
|[方法: カスタム サイト定義と構成を作成します。](http://go.microsoft.com/fwlink/?LinkId=183309)|既存のサイト定義をコピーし、そのコピーを変更することで、SharePoint でカスタム サイト定義を作成する方法について説明します。|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|**\[新しい SharePoint サイト\]** ページの **\[テンプレートの選択\]** セクションに表示される、サイト定義を指定するための元のファイルについて説明します。|  
|[SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)|SharePoint ソリューションをグローバルに使用するための準備方法について説明します。|  
|[SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)|ユーザーが変更できる SharePoint ページのパーツの作成方法について説明します。|  
|[Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|アプリケーション ページと Web パーツで動作する再利用可能なコントロールの作成方法についてを説明します。|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|プロジェクトで Web ページを開くと表示されるデザイナーの使用方法について説明します。|  
|[ASP.NET Web Pages Overview](http://go.microsoft.com/fwlink/?LinkId=178726)|[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Web ページの構造、[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] によるページの処理方法、および [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ページでの XHTML 標準に準拠したマークアップの表示方法に関する一般情報について説明します。|  
|[ASP.NET Web ページの構文](http://go.microsoft.com/fwlink/?LinkId=178727)|ASP.NET ページを構成するマークアップ要素について説明します。|  
|[ASP.NET Web ページのプログラミング](http://go.microsoft.com/fwlink/?LinkId=178728)|[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ページにイベント ハンドラーを作成する方法およびクライアント スクリプトを操作する方法について説明します。|  
|[Windows SharePoint Services のプログラミング](http://go.microsoft.com/fwlink/?LinkId=178729)|[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] に用意されているマネージ オブジェクト モデルの使用方法について説明します。|  
  
## 参照  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  