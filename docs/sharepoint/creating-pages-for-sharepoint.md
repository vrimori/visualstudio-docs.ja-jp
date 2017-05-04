---
title: "SharePoint 用ページの作成 | Microsoft Docs"
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
helpviewer_keywords: 
  - "コンテンツ ページ [Visual Studio での SharePoint 開発], デザイン"
  - "マスター ページ [Visual Studio での SharePoint 開発], デザイン"
  - "ページ レイアウト [Visual Studio での SharePoint 開発], デザイン"
  - "Visual Studio での SharePoint 開発, コンテンツ ページ"
  - "Visual Studio での SharePoint 開発, マスター ページ"
  - "Visual Studio での SharePoint 開発, ページ レイアウト"
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# SharePoint 用ページの作成
  SharePoint サイト用のアプリケーション ページ、サイト ページ、マスター ページ、およびページ レイアウトを作成できます。  
  
 アプリケーション ページは、Visual Studio のテンプレートを使用して作成できます。  サイト ページ、マスター ページ、およびページ レイアウトは、SharePoint Designer を使用して作成します。  作成したページを Visual Studio にインポートして、SharePoint プロジェクトで使用できます。  
  
 また、カスケード スタイル シート、ECMAScript、およびテーマを使用して、ページの外観と動作を変更できます。  
  
## SharePoint ページの種類  
 次の表では、SharePoint サイトに含まれる 4 種類の主要なページについて説明します。  
  
|ページの種類|説明|  
|------------|--------|  
|アプリケーション ページ|カスタム コードを含むページまたは複数のサイトで共有するページが必要な場合は、アプリケーション ページを作成します。  それ以外の場合は、サイト ページが最善の選択です。|  
|サイト ページ|次のいずれかのタスクを実行する場合は、サイト ページを作成します。<br /><br /> -   SharePoint ライブラリにページを追加する。<br />-   動的な Web パーツや Web パーツ ゾーンなどの機能をページでホストできるようにする。<br />-   ユーザーが SharePoint Designer を使用してページをカスタマイズできるようにする。<br /><br /> カスタム コードを含むページが必要である場合は、サイト ページを作成しないでください。  サイト ページにもカスタム コードを追加できますが、SharePoint Designer を使用してページをカスタマイズすると、コードの実行が停止します。|  
|マスター ページ|サイト ページとアプリケーション ページに共通の構造を定義する場合は、マスター ページを作成します。|  
|ページ レイアウト|ページ レイアウトは [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] に固有の機能であり、サイト ページとアプリケーション ページに共通の構造をさらに詳しく定義できます。|  
  
 各ページの種類の概要については、"を [ビルド ブロック: ページおよびユーザー インターフェイス](http://go.microsoft.com/fwlink/?LinkID=182095)参照してください [ページ レイアウトとマスター ページ](http://go.microsoft.com/fwlink/?LinkID=182096)。  
  
## アプリケーション ページの作成  
 SharePoint プロジェクトに**アプリケーション ページ**項目を追加することで、Visual Studio でアプリケーション ページを作成できます。  ページにコントロールを追加した後、コードを追加してコントロール イベントを処理できます。  
  
 追加の構成手順を実行しなくても、ページのコード ファイルへのブレークポイントの設定、デバッガーの開始、およびローカルな SharePoint サイトでのページのテストを実行できます。  詳細については、「[SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)」を参照してください。  
  
## サイト ページ、マスター ページ、ページ レイアウトの作成  
 SharePoint Designer を使用して、サイト ページ、マスター ページ、およびページ レイアウトを作成できます。  その後、作成したページを Visual Studio にインポートできます。  Visual Studio の配置機能またはソース管理機能を利用する場合は、ページをインポートします。  詳細については、「[既存の SharePoint サイトからのアイテムのインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)」を参照してください。  
  
 インポートした後でこれらのページを簡単に変更できないため、インポートする前にページを設計する必要があります。  
  
## カスケード スタイル シート、ECMAScript、およびテーマの作成  
 Visual Studio には、SharePoint サイト用のカスケード スタイル シート \(CSS\)、ECMAScript \(JavaScript、JScript\)、またはテーマ ファイルを作成するためのテンプレートはありません。  これらのファイルは、SharePoint SDK のガイダンスを使用して、または SharePoint Designer などのツールを使用して作成できます。  
  
 これらのファイルは、ソリューションに直接追加することも、インポートすることもできます。  どちらの場合も、追加する項目ごとに適切にマップされたフォルダーを作成する必要があります。  マップされたフォルダーの作成方法の詳細については、「[方法: マップされたフォルダーを追加および削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)」を参照してください。  
  
 カスケード スタイル シートの作成に関する詳細については、参照 [SharePoint Foundation のカスケード スタイル シート クラスの使用](http://go.microsoft.com/fwlink/?LinkID=182098)します。  SharePoint ソリューション用の JavaScript ファイルおよび JScript ファイルの作成の詳細については、参照します [ECMAScript の基本の ASPX ページの設定](http://go.microsoft.com/fwlink/?LinkID=182099)。  テーマの詳細については、参照します [ビルド ブロック: ページおよびユーザー インターフェイス](http://go.microsoft.com/fwlink/?LinkID=182095)。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)|アプリケーション ページ \(SharePoint のマスター ページとマージされる .aspx コンテンツ\) を追加する方法を説明します。|  
|[方法: アプリケーション ページを作成する](../sharepoint/how-to-create-an-application-page.md)|SharePoint サイトで実行される ASP.NET ページを作成する方法について説明します。|  
|[チュートリアル: SharePoint アプリケーション ページの作成](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|SharePoint サイトの ASP.NET Web ページをデザインおよびデバッグする方法について説明します。|  
|[Visual Web Developer の操作](http://msdn.microsoft.com/ja-jp/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|プロジェクトで Web ページを開くと表示されるデザイナーの使用方法について説明します。|  
  
  