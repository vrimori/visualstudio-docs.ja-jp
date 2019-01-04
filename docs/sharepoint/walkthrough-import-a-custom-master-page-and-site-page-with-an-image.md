---
title: 'チュートリアル: カスタム マスター ページをインポートし、サイトのページ イメージ |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f7901bfea334ff3d9ad6d197bf64b3f1a87961a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904154"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>チュートリアル: カスタム マスター ページとサイトのページにイメージをインポートします。
  このチュートリアルの SharePoint カスタム マスター ページとサイトのページにイメージがインポートする方法、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクト。  

 このチュートリアルでは、以下のタスクを完了する方法について説明します。  

- SharePoint Designer で、イメージを使用して、カスタム マスター ページとサイトのページを作成します。  

- SharePoint ソリューションにカスタム マスター ページ、画像、およびサイト ページをエクスポート (*.wsp*) ファイル。  

- インポートおよび展開、 *.wsp*ファイルを[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint ソリューション パッケージのインポート プロジェクトを使用して SharePoint プロジェクト。  

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  

## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するには、次のコンポーネントが必要です。  

-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。  

-   Visual Studio  

-   SharePoint Designer 2010。  

## <a name="create-items-in-sharepoint-designer"></a>SharePoint Designer で項目を作成します。
 この例は、SharePoint Designer でエクスポートの 3 つの項目を作成する方法を示しています。 カスタム マスター ページ、カスタム マスター ページ、およびサイト ページに表示するイメージ ファイルを参照しているサイト ページ。 イメージは、SharePoint の/images/フォルダーに追加されます。  

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>SharePoint Designer で独自のマスター ページを作成するには

1.  SharePoint Designer のナビゲーション ウィンドウで選択、**マスター ページ**サイト オブジェクト。  

2.  **マスター ページ**リボンで、選択**空白のマスター ページ**します。  

3.  新しいマスター ページを選択し、**マスター ページ**リボンで、選択**ファイルの編集**します。  

4.  SharePoint Designer の下部にある、選択、**コード**タブ。  

5.  既存のマークアップを次のマークアップに置き換えます。  

    ```aspx-csharp  
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

6.  ページの保存、**マスター ページ**タブをクリックし、マスター ページの名前を変更**mybasic1.master**します。  

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint Designer でコンテンツ データベースにイメージを追加します。
 今すぐサイト ページに表示するイメージを追加することができます。 イメージは、SharePoint コンテンツ データベースにデプロイされます。  

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint Designer でのコンテンツ データベースにイメージを追加するには

1.  ナビゲーション ウィンドウで選択、**すべてのファイル**サイト オブジェクト、およびその後、ツリー ビューで次のように選択します。、**イメージ**フォルダー。  

2.  **すべてのファイル**リボンで、選択**ファイルをインポートする**、任意のファイルを選択し、、 **OK**ボタン。 この例では、ファイルの名前は**myimg1.png**します。  

     必要に応じて、画像を整理するためにサブフォルダーを作成することができます。  

3.  閉じる、**インポート** ダイアログ ボックス。  

## <a name="create-a-site-page"></a>サイト ページを作成します。
 この基本的なサイト ページは、カスタム マスター ページを使用し、前の手順で追加したイメージを表示します。  

#### <a name="to-create-a-site-page"></a>サイトのページを作成するには  

1.  ナビゲーション ウィンドウで選択、**サイト ページ**オブジェクト。  

2.  **ページ**リボンで、選択、**ページ** ボタンを選択、 **ASPX**ページの種類と、新しいファイルを名前**mycontentpage1.aspx**します。  

     必要に応じて、サイトのページを整理するためにサブフォルダーを作成することができます。  

3.  サイトのページの一覧に次のように選択します。 **MyContentPage1.aspx**をそのプロパティ ページを開き、次に、ページの下部には、次のように選択します。、**ファイルの編集**リンク。  

     メッセージが表示しこのページには、セーフ モードで編集可能な任意のリージョンにはが含まれていないことを示すされ高度なモードでこのページを開き、選択するかどうかを確認する場合、**はい**ボタンをクリックします。  

4.  ページの下部にある、選択、**コード**ボタンをクリックします。  

5.  既存のマークアップを次のマークアップに置き換えます。  

    ```aspx-csharp  
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

## <a name="export-the-items-from-sharepoint"></a>SharePoint からのアイテムをエクスポートします。
 SharePoint ソリューションを SharePoint からアイテムをエクスポート (*.wsp*) ファイル。  

#### <a name="to-export-items-from-sharepoint-designer"></a>SharePoint Designer からアイテムをエクスポートするには

1.  SharePoint Designer のナビゲーション ウィンドウで選択、**チーム サイト**オブジェクト、し、**サイト**リボンで、選択**テンプレートとして保存**します。  

2.  **テンプレートとして保存** ダイアログ ボックスに、ファイル名とテンプレート名を入力、**コンテンツを含む**チェック ボックスをオンにして、 **ok**ボタンをクリックします。  

     これは、サイトの内容を保存します、 *.wsp*ファイル。  

3.  ソリューションがエクスポートした後は、選択、**ソリューション ギャラリー**リンクの使用可能なソリューション ファイルの一覧を表示します。  

4.  ショートカット メニューを開き、新しい *.wsp*ファイルを選び、**として保存ターゲット**システムに保存します。  

## <a name="import-the-items-into-visual-studio"></a>Visual Studio にアイテムをインポートします。
 インポート、 *.wsp*ファイルを[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 コンテンツをインポートすると後、は、カスタマイズにより多くの項目を追加し、デプロイします。  

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Visual Studio に .wsp ファイルからアイテムをインポートするには  

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、作成、 **SharePoint 2010 ソリューション パッケージのインポート**プロジェクト。  

2. **をインポートする項目の選択**] ページ [**モジュール**で、**型**列で、インポートについては、次の表に、ファイルのみのチェック ボックスをオンします。  


   | ファイル名 | 説明 |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | カスタム マスター ページです。 |
   | images_ | SharePoint のファイル システムのイメージ ファイルです。 |
   | SitePages_ | サイトのページ。 |


3. 選択、**完了**ボタンをクリックして選択したアイテムをインポートします。  

4. **ソリューション エクスプ ローラー**、選択、 \_catalogsmasterpage\_ノードの値を設定およびその**配置競合の解決**プロパティを**自動**.  

    これにより、配置の競合が自動的に解決されることを確認できます。  

5. 新しいマスター ページに同じ名前の既存のページがある場合は、既存のページが既定のマスター ページまたは SharePoint Designer でカスタム マスター ページのいずれかとしてマークされていないことを確認します。  

    既存のマスター ページは、既定のマスター ページまたはカスタム マスター ページのいずれかとしてマークすると、マスター ページを削除できないことを示す配置エラーが発生します。 この問題を回避するには、これの操作を行います。  

   -   既存のマスター ページが既定のマスター ページとして設定されている場合、既定のマスター ページとして別のマスター ページを一時的に設定します。 ファイルを SharePoint に配置した後は、既定のマスター ページとして、新しいマスター ページを設定します。  

   -   既存のマスター ページは、カスタム マスター ページとして設定されている場合、カスタム マスター ページとして一時的に別のマスター ページを設定します。 ファイルを SharePoint に配置した後は、カスタム マスター ページとして、新しいマスター ページを設定します。  

6. メニュー バーで、**ビルド** > **ソリューションの配置**します。  

7. 展開済みのアイテムを表示する SharePoint サイトを開きます。  

   ファイルをインポートする別の方法[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]それらのモジュールにファイルを追加する SharePoint は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [操作方法：マスター ページまたはテーマをインポート](../sharepoint/how-to-import-a-master-page-or-theme.md)と[モジュールを使用してファイルをソリューションに含める](../sharepoint/using-modules-to-include-files-in-the-solution.md)します。  

## <a name="see-also"></a>関連項目
 [既存の SharePoint サイトからのアイテムのインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint ソリューションを開発します。](../sharepoint/developing-sharepoint-solutions.md)   
 [Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成します。](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
