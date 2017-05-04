---
title: "SharePoint のアプリケーション ページの作成 | Microsoft Docs"
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
  - "アプリケーション ページ [Visual Studio での SharePoint 開発], 作成"
  - "アプリケーション ページ [Visual Studio での SharePoint 開発], 開発"
  - "Visual Studio での SharePoint 開発, アプリケーション ページ"
  - "Visual Studio での SharePoint 開発, コンテンツ ページ"
  - "Visual Studio での SharePoint 開発, Web ページ"
ms.assetid: a6e97149-15dd-4bdb-8d75-3b53f886f76c
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# SharePoint のアプリケーション ページの作成
  *アプリケーション ページ*は、SharePoint Web サイトで使用するためにデザインされた ASP.NET Web ページです。  アプリケーション ページは、特殊な種類の ASP.NET ページです。  アプリケーション ページと標準的な ASP.NET ページの主な違いは、アプリケーション ページには SharePoint マスター ページとマージされるコンテンツが含まれる点です。  マスター ページを使用すると、アプリケーション ページはサイト上の他のページと同じ外観と動作を共有できます。  
  
 Visual Studio では、デザイナーを使用してアプリケーション ページをデザインできます。  デザイナーには、マスター ページに定義された各コンテンツ プレースホルダーのコンテンツ領域が表示されます。  このコンテンツ領域にコントロールをドラッグして、アプリケーション ページをデザインできます。  
  
## アプリケーション ページ  
 アプリケーション ページはサーバー上のすべてのサイトで共有されますが、サイト ページは 1 つのサイトに固有のページです。  詳細について。[SharePoint ページの種類](http://go.microsoft.com/fwlink/?LinkID=211584)  
  
 既定では、SharePoint サイトを作成するときに表示されるページのほとんどは、サイト ページです。  サイト ページは SharePoint ページ ライブラリに追加できます。  SharePoint デザイナーなどのツールを使用して、サイト ページをカスタマイズすることもできます。  また、サイト ページでは、動的な Web パーツや Web パーツ領域などの機能をホストすることもできます。  
  
 アプリケーション ページにこのような機能を備えることはできません。  ただし、ページにカスタム コードを含める場合、アプリケーション ページの作成をお勧めします。  サイト ページにもカスタム コードを追加できますが、ユーザーが SharePoint デザイナーなどのツールを使用してページをカスタマイズすると、コードの実行が停止します。  
  
> [!NOTE]  
>  Visual Studio には、SharePoint サイトのサイト ページを作成するためのテンプレートがありません。  詳細については、参照します [SharePoint ページの種類](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
## アプリケーション ページを作成する  
 アプリケーション ページを作成するには、SharePoint プロジェクトに**アプリケーション ページ**項目を追加します。  アプリケーション ページを作成すると、プロジェクトに次のフォルダーが追加されます。  
  
|フォルダー|説明|  
|-----------|--------|  
|レイアウト|SharePoint ファイル システムの \_layouts 仮想ディレクトリにマップされます。|  
|レイアウトのサブフォルダー|アプリケーション ページを構成するファイルが含まれます。  既定では、このフォルダー名はプロジェクト名と同じです。  このフォルダー名はいつでも変更できます。  プロジェクトを実行すると、SharePoint ファイル システムの \_layouts 仮想ディレクトリにこのフォルダーが配置されます。|  
  
 プロジェクトに次のファイルが追加されます。  
  
|File|説明|  
|----------|--------|  
|ASP.NET ページ ファイル \(.aspx\)|ページを定義する XML マークアップを含みます。|  
|アプリケーション ページのコード ファイル|アプリケーション ページの分離コードを含みます。  このファイルにイベントを処理するコードを追加します。|  
|アプリケーション ページのデザイナー コード ファイル|デザイナーによって生成されたコードを含みます。  このファイルは直接編集しないでください。|  
  
## アプリケーション ページのデザインとデバッグ  
 Visual Studio の Visual Web Developer デザイナーを使用して、アプリケーション ページのコンテンツをデザインします。  このデザイナーは、プロジェクトのアプリケーション ページを開くと表示されます \(によりまたはショートカット メニューを開き、**\[開く\]** をクリックしますダブルクリックするなど\)。  この方法の詳細についてはこのデザイナーを使用する [Visual Studio Web Development Content Map](http://msdn.microsoft.com/ja-jp/9c31f93b-c8fb-4599-9b14-6194ec8c7539)を参照します。  
  
> [!NOTE]  
>  デザイナーの **\[ソース\]** ビューの専用のページをデザインできます。  デザイナーの**デザイン** ビューは、アプリケーション ページの場合は無効になります。  
  
 Visual Studio で他の SharePoint プロジェクト項目をデバッグする場合と同様に、アプリケーション ページをデバッグできます。  Visual Studio デバッガーを開始すると、SharePoint サイトが開きます。  
  
 アプリケーション ページを表示するには、アプリケーション ページの場所に手動で移動する必要があります \(例: http:\/\/*Server\_Name*\/\_layouts\/*Project\_Name*\/ApplicationPage1.aspx\)。  
  
 SharePoint プロジェクトのデバッグ方法の詳細については、「[SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)」を参照してください。  
  
## マスター ページの選択  
 既定で、**アプリケーション ページ**項目は、プロジェクトのデバッグに使用しているサイトのマスター ページを参照しています。  このページ名は v4.master で、SharePoint サイトの **\[マスター ページ ギャラリー\]** の一覧から検索できます。  
  
 アプリケーション ページから使用するマスター ページを明示的に変更するには、アプリケーションの `Page` 要素の `MasterPageFile` 属性を設定します。\(たとえば、「`MasterPageFile="~/_layouts/applicationv4.master"`」と指定します\)。  実際、SharePoint サーバーで動的マスター ページが有効にされていない場合、この属性を設定する必要があります。  SharePoint のマスター ページの詳細については、参照します [マスター ページ](http://go.microsoft.com/fwlink/?LinkID=169281)。  
  
## 参照  
 [詳細な SharePoint Foundation の開発](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [ASP.NET Web ページの概要](../Topic/ASP.NET%20Web%20Forms%20Pages%20Overview.md)   
 [ASP.NET Web ページの構文の概要](../Topic/ASP.NET%20Web%20Forms%20Page%20Syntax%20Overview.md)   
 [ASP.NET Web ページのプログラミング](http://msdn.microsoft.com/ja-jp/5626c661-8057-4de8-b658-c2e35ed4b4c9)  
  
  