---
title: "チュートリアル: イメージを備えたカスタム マスター ページおよびサイト ページのインポート"
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
  - "インポート (項目を) [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, インポート (項目を)"
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# チュートリアル: イメージを備えたカスタム マスター ページおよびサイト ページのインポート
  このチュートリアルでは、SharePoint カスタム マスター ページとイメージが含まれているサイト ページを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトにインポートする方法について説明します。  
  
 このチュートリアルで説明する内容は次のとおりです。  
  
-   SharePoint Designer でカスタム マスター ページを作成し、イメージを使用してサイト ページを作成する。  
  
-   カスタム マスター ページ、イメージ、およびサイト ページを SharePoint ソリューション \(.wsp\) ファイルにエクスポートする。  
  
-   .wsp ファイルを、\[SharePoint ソリューション パッケージのインポート\] パッケージを使用して [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトにインポートして配置する。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを完了するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] および SharePoint。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio  
  
-   SharePoint Designer 2010。  
  
## SharePoint Designer で項目を作成する  
 この例では、エクスポートする 3 つの項目 \(カスタム マスター ページ、カスタム マスター ページを参照するサイト ページ、およびサイト ページに表示されるイメージ ファイル\) を SharePoint Designer で作成する方法を示します。  イメージは SharePoint の \/images\/ フォルダーに追加されます。  
  
#### SharePoint Designer でカスタム マスター ページを作成するには  
  
1.  SharePoint Designer のナビゲーション ペインで、**\[マスター ページ\]** サイト オブジェクトを選択します。  
  
2.  **\[マスター ページ\]** のリボンで、**\[空白のマスター ページ\]** をクリックします。  
  
3.  次に、新しいマスター ページを、**\[マスター ページ\]** のリボンで選択し、**\[ファイルの編集\]** をクリックします。  
  
4.  SharePoint Designer で、**\[コード\]** タブをクリックします。  
  
5.  既存のモジュールのマークアップを次のマークアップに置き換えます。  
  
    ```  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  
  
6.  ページを保存し、**\[マスター ページ\]** タブを選択し、**mybasic1.master**としてマスター ページの名前を変更します。  
  
## SharePoint Designer でイメージをコンテンツ データベースに追加する  
 次に、サイト ページに表示するイメージを追加できます。  イメージは、SharePoint コンテンツ データベースに配置されます。  
  
#### SharePoint Designer でイメージをコンテンツ データベースに追加するには  
  
1.  次にナビゲーション ペインで、**\[すべてのファイル\]** サイト オブジェクトを、ツリー ビューで選択して **\[イメージ\]** フォルダーを選択します。  
  
2.  **\[すべてのファイル\]** のリボンで、**\[ファイルのインポート\]** をクリックします、ファイルの選択をクリックし、**\[OK\]** ボタンをクリックします。  この例では、**myimg1.png** という名前のファイルを選択します。  
  
     オプションとして、イメージを整理するためのサブフォルダーを作成できます。  
  
3.  **\[インポート\]** ダイアログ ボックスを閉じます。  
  
## サイト ページを作成する  
 この基本的なサイト ページでは、カスタム マスター ページを使用して前の手順で追加したイメージを表示します。  
  
#### サイト ページを作成するには  
  
1.  ナビゲーション ペインで、**\[サイトのページ\]** オブジェクトを選択します。  
  
2.  **\[ページ\]** のリボンで、**\[ページ\]** ボタンを選択し、**\[ASPX\]** ページの種類を選択し、新しいファイル **mycontentpage1.aspx**という名前を付けます。  
  
     オプションとして、サイト ページを整理するためのサブフォルダーを作成できます。  
  
3.  次に、サイト ページでは、ページの下部にあるプロパティ ページを選択し、開くをクリックします **\[ファイルの編集\]** リンクを選択し、**\[MyContentPage1.aspx\]** をクリックします。  
  
     メッセージが表示され、このページはセーフ モードで編集できる含まれておらず、詳細設定モードでこのページを表示するかどうかを今後このメッセージ領域を言ったら **\[はい\]** ボタンをクリックします。  
  
4.  ページの下部に、**\[コード\]** ボタンをクリックします。  
  
5.  既存のモジュールのマークアップを次のマークアップに置き換えます。  
  
    ```  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  
  
    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  
  
6.  更新したサイト ページを保存します。  
  
## SharePoint から項目をエクスポートする  
 項目を SharePoint から SharePoint ソリューション \(.wsp\) ファイルにエクスポートします。  
  
#### SharePoint から項目をエクスポートするには  
  
1.  次に、SharePoint Designer のナビゲーション ペインで、**\[チーム サイト\]** オブジェクトを、**\[サイト\]** のリボンで、**\[テンプレートとして保存\]** をクリックしますを選択します。  
  
2.  **\[テンプレートとして保存\]** ダイアログ ボックスで、ファイル名とテンプレート名を入力し、**\[コンテンツを含む\]** のチェック ボックスをオンにし、**\[OK\]** ボタンをクリックします。  
  
     これで、サイトのコンテンツが .wsp ファイルに保存されます。  
  
3.  ソリューションをエクスポートすると、使用可能なソリューション ファイルの一覧を表示するに **\[ソリューション ギャラリー\]** リンクをクリックします。  
  
4.  新しい .wsp ファイルのショートカット メニューを開き、システムに保存するに **\[対象をファイルに保存\]** をクリックします。  
  
## 項目を Visual Studio にインポートする  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]に .wsp ファイルをインポートします。  インポートしたコンテンツ、カスタマイズ、項目を追加し、これを配置します。  
  
#### .wsp ファイルから Visual Studio に項目をインポートするには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で、**\[SharePoint 2010 ソリューション パッケージのインポート\]** のプロジェクトを作成します。  
  
2.  **\[種類\]** 列の **\[モジュール\]** の **\[インポートする項目の選択\]** ページで、インポートの次の表のファイルのみチェック ボックスをオンにします。  
  
    |ファイル名|説明|  
    |-----------|--------|  
    |\_catalogsmasterpage\_|カスタム マスター ページです。|  
    |images\_|SharePoint ファイル システム内のイメージ ファイルです。|  
    |SitePages\_|サイト ページです。|  
  
3.  選択した項目をインポートするに **\[完了\]** ボタンをクリックします。  
  
4.  **\[ソリューション エクスプローラー\]** で、\_catalogsmasterpage\_ノードを選択し、**\[自動\]** に **\[配置競合の解決\]** のプロパティの値を設定します。  
  
     これにより、配置競合を自動的に解決できます。  
  
5.  新しいマスター ページの名前が既存のページと同じである場合は、SharePoint Designer で既存のページが "既定のマスター ページ" または "カスタム マスター ページ" としてマークされていないことを確認します。  
  
     既存のマスター ページが、既定のマスター ページまたはカスタム マスター ページとしてマークされている場合、マスター ページを削除できないことを示す配置エラーが発生します。  この問題を回避するには、次を実行します。  
  
    -   既存のマスター ページが既定のマスター ページとして設定されている場合は、別のマスター ページを一時的に既定のマスター ページとして設定します。  ファイルを SharePoint に配置した後、新しいマスター ページを既定のマスター ページとして設定します。  
  
    -   既存のマスター ページがカスタム マスター ページとして設定されている場合は、別のマスター ページを一時的にカスタム マスター ページとして設定します。  ファイルを SharePoint に配置した後、新しいマスター ページをカスタム マスター ページとして設定します。  
  
6.  メニュー バーで、**\[ソリューションの配置\]\[ビルド\]** をクリックします。  
  
7.  SharePoint サイトを開いて、配置された項目を表示します。  
  
 ファイルを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] にインポートして SharePoint に配置する別の方法として、ファイルを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のモジュールに追加することもできます。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)]「[方法: マスター ページまたはテーマをインポートする](../sharepoint/how-to-import-a-master-page-or-theme.md)」および「[モジュールを使用してソリューションにファイルを追加する](../sharepoint/using-modules-to-include-files-in-the-solution.md)」を参照してください。  
  
## 参照  
 [既存の SharePoint サイトからのアイテムのインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  