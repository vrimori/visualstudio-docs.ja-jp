---
title: "チュートリアル: カスタム マスター ページのインポートし、サイトのイメージでページ |Microsoft ドキュメント"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ef55a90b55314bf7ab2c5aa6259f09b62a350da3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>チュートリアル: イメージを備えたカスタム マスター ページおよびサイト ページのインポート
  このチュートリアルは、SharePoint カスタム マスター ページとサイトのページにイメージがインポートする方法を示します、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクト。  
  
 このチュートリアルでは、以下のタスクを完了する方法について説明します。  
  
-   SharePoint Designer でイメージを使用してカスタム マスター ページ、およびサイト ページを作成します。  
  
-   カスタム マスター ページ、イメージ、およびサイトのページを SharePoint ソリューション (.wsp) ファイルにエクスポートします。  
  
-   インポートして、.wsp ファイルの展開、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ソリューション パッケージのインポート プロジェクトを使用して SharePoint プロジェクト。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行する次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio  
  
-   SharePoint Designer 2010。  
  
## <a name="create-items-in-sharepoint-designer"></a>SharePoint Designer で項目を作成します。  
 この例は、エクスポートの SharePoint Designer の 3 つの項目を作成する方法を示します: カスタム マスター ページ、カスタムのマスター ページ、およびサイトのページに表示するイメージ ファイルを参照しているサイトのページです。 SharePoint で/images/フォルダーには、画像を追加します。  
  
#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>SharePoint デザイナーでカスタム マスター ページを作成するには  
  
1.  SharePoint Designer のナビゲーション ウィンドウで、選択、**マスター ページ**サイト オブジェクトです。  
  
2.  **マスター ページ**リボンで、選択**空白マスター ページ**です。  
  
3.  新しいマスター ページを選択し、、**マスター ページ**リボンで、選択**ファイルの編集**です。  
  
4.  SharePoint Designer の下部にある、選択、**コード**タブです。  
  
5.  既存のマークアップを次のマークアップに置き換えます。  
  
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
  
6.  ページの保存、**マスター ページ**タブをクリックし、マスター ページの名前を変更**mybasic1.master**です。  
  
## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint Designer でコンテンツ データベースにイメージを追加します。  
 今すぐサイトのページに表示するイメージを追加することができます。 イメージは、SharePoint コンテンツ データベースに配置されます。  
  
#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint Designer でコンテンツ データベースにイメージを追加するには  
  
1.  ナビゲーション ウィンドウで、選択、**すべてのファイル**サイト オブジェクト、およびツリー ビューを選択、**イメージ**フォルダーです。  
  
2.  **すべてのファイル**リボンで、選択**ファイルをインポートする**、任意のファイルを選択し、、 **OK**ボタンをクリックします。 この例では、ファイルの名前は**myimg1.png**です。  
  
     必要に応じて、画像を整理するためにサブフォルダーを作成することができます。  
  
3.  閉じる、**インポート** ダイアログ ボックス。  
  
## <a name="create-a-site-page"></a>サイト ページを作成します。  
 この基本的なサイトのページでは、カスタム マスター ページを使用し、前の手順で追加したイメージを表示します。  
  
#### <a name="to-create-a-site-page"></a>サイト ページを作成するには  
  
1.  ナビゲーション ウィンドウで、選択、**サイト ページ**オブジェクト。  
  
2.  **ページ**リボンで、選択、**ページ** ボタンを選択して、 **ASPX**の種類 ページをクリックし、新しいファイルを名**mycontentpage1.aspx**です。  
  
     必要に応じて、サイトのページを整理するためにサブフォルダーを作成することができます。  
  
3.  一覧で、サイト ページ、 **MyContentPage1.aspx**をそのプロパティ ページを開き、次に、ページの下部には、次のように選択します。、**編集ファイル**リンクします。  
  
     メッセージが表示しこのページがセーフ モードで編集可能な領域が含まれていないことを示すされ、高度なモードでこのページを開き、選択するかどうかを確認する場合、**はい**ボタンをクリックします。  
  
4.  ページの下部にある、選択、**コード**ボタンをクリックします。  
  
5.  既存のマークアップを次のマークアップに置き換えます。  
  
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
  
6.  更新されたサイトのページを保存します。  
  
## <a name="export-the-items-from-sharepoint"></a>Sharepoint サイトから、項目をエクスポートします。  
 SharePoint からのアイテムを SharePoint ソリューション (.wsp) ファイルにエクスポートします。  
  
#### <a name="to-export-items-from-sharepoint-designer"></a>SharePoint Designer からアイテムをエクスポートするには  
  
1.  SharePoint Designer のナビゲーション ウィンドウで、選択、**チーム サイト**オブジェクト、、**サイト**リボンで、選択**テンプレートとして保存**です。  
  
2.  **テンプレートとして保存** ダイアログ ボックスで、ファイル名とテンプレート名を入力、**コンテンツを含む**チェック ボックスをオンにして、 **ok**ボタンをクリックします。  
  
     これには、.wsp ファイルに、サイトのコンテンツが保存されます。  
  
3.  後で、ソリューションがエクスポート、**ソリューション ギャラリー**利用可能なソリューション ファイルの一覧を表示するリンクです。  
  
4.  新しい .wsp ファイルのショートカット メニューを開き、選択**として保存ターゲット**をシステムに保存します。  
  
## <a name="import-the-items-into-visual-studio"></a>Visual Studio にアイテムをインポートします。  
 .Wsp ファイルをインポート[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 コンテンツをインポートした後は、カスタマイズに他のアイテムを追加してから展開します。  
  
#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Visual Studio に .wsp ファイルからアイテムをインポートするには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、作成、 **SharePoint 2010 ソリューション パッケージのインポート**プロジェクト。  
  
2.  **をインポートする項目の選択**] ページの [**モジュール**で、**型**列で、インポート用の次の表に、ファイルのみのチェック ボックスをオンします。  
  
    |ファイル名|説明|  
    |---------------|-----------------|  
    |_catalogsmasterpage\_|カスタム マスター ページです。|  
    |images_|SharePoint のファイル システムのイメージ ファイルです。|  
    |SitePages_|サイトのページです。|  
  
3.  選択、**完了**ボタンをクリックして選択したアイテムをインポートします。  
  
4.  **ソリューション エクスプ ローラー**、_catalogsmasterpage を選択\_ ノードの値を設定およびその**配置競合の解決**プロパティを**自動**です。  
  
     これにより、展開の競合が自動的に解決されることを確認できます。  
  
5.  新しいマスター ページに同じ名前の既存のページがある場合は、既存のページがない既定のマスター ページまたは SharePoint デザイナーでカスタム マスター ページのいずれかとしてマークされていることを確認します。  
  
     既存のマスター ページがマスター ページの既定またはカスタム マスター ページとしてマークされている場合は、マスター ページを削除できないことを示す配置エラーが発生します。 この問題を避けるためには、この操作を行います。  
  
    -   既存のマスター ページが既定のマスター ページとして設定されている場合、マスター ページの既定として別のマスター ページを一時的に設定します。 ファイルを SharePoint に配置した後は、既定のマスター ページとして、新しいマスター ページを設定します。  
  
    -   既存のマスター ページは、カスタム マスター ページとして設定されている場合、カスタム マスター ページとして一時的に別のマスター ページを設定します。 ファイルを SharePoint に配置した後は、カスタム マスター ページとして、新しいマスター ページを設定します。  
  
6.  メニュー バーで、次のように選択します。**ビルド**、**ソリューションの配置**です。  
  
7.  展開されたアイテムを表示する SharePoint サイトを開きます。  
  
 ファイルをインポートする代替方法[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]しを展開内のモジュールにファイルを追加するは、SharePoint[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][する方法: マスター ページまたはテーマをインポート](../sharepoint/how-to-import-a-master-page-or-theme.md)と[モジュールを使用して、ソリューション内のファイルのインクルード](../sharepoint/using-modules-to-include-files-in-the-solution.md)です。  
  
## <a name="see-also"></a>参照  
 [既存の SharePoint サイトからアイテムをインポートします。](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  