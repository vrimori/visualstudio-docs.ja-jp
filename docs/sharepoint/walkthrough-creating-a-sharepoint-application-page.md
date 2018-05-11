---
title: 'チュートリアル: SharePoint アプリケーション ページの作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 21191ec585b83099aefad4f1c43949ba94cfc4ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-sharepoint-application-page"></a>チュートリアル: SharePoint アプリケーション ページの作成
 
アプリケーション ページとは、特殊なフォームの ASP.NET ページです。 アプリケーション ページには、SharePoint のマスター ページとマージされるコンテンツが含まれます。 詳細については、次を参照してください。 [for SharePoint アプリケーション ページを作成する](../sharepoint/creating-application-pages-for-sharepoint.md)です。

このチュートリアルでは、アプリケーション ページを作成し、そのページをローカル SharePoint サイトを使ってデバッグする方法を説明します。 このページには、サーバー ファーム上のあらゆるサイトで、各ユーザーが作成または変更したすべての項目が表示されます。

このチュートリアルでは、次の作業について説明します。

- SharePoint プロジェクトを作成する
- SharePoint プロジェクトにアプリケーション ページを追加する
- アプリケーション ページに ASP.NET コントロールを追加する
- ASP.NET コントロールに分離コードを追加する
- アプリケーション ページをテストする

> [!NOTE]
> 次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

- サポート対象エディションの Windows と SharePoint 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。

## <a name="creating-a-sharepoint-project"></a>SharePoint プロジェクトを作成する

最初に、作成、**空の SharePoint プロジェクト**です。 後で、追加する、**アプリケーション ページ**項目をこのプロジェクトにします。

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。

2. 開く、**新しいプロジェクト**] ダイアログ ボックスで、展開、 **Office/sharepoint** [クリックしてを使用する言語のノード、 **SharePoint ソリューション**ノード。

3. **Visual Studio のインストールされたテンプレート** ウィンドウで、選択、 **SharePoint 2010 - 空のプロジェクト**テンプレート。 プロジェクトに名前を**MySharePointProject**を選択し、 **OK**ボタンをクリックします。

     **SharePoint カスタマイズ ウィザード**が表示されます。 このウィザードを使用すると、プロジェクトのデバッグに使用するサイトや、ソリューションの信頼レベルを選択できます。

4. 選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、**完了**ボタンをクリックして既定のローカル SharePoint サイトです。

## <a name="creating-an-application-page"></a>アプリケーション ページを作成する

アプリケーション ページを作成するには追加、**アプリケーション ページ**プロジェクト項目です。

1. **ソリューション エクスプ ローラー**、選択、 **MySharePointProject**プロジェクト。

2. メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。

3. **新しい項目の追加** ダイアログ ボックスで、選択、**アプリケーション ページ (ファーム ソリューションのみ**テンプレート。

4. ページの名前を付けます**SearchItems**を選択し、**追加**ボタンをクリックします。

     Visual Web Developer デザイナーには、[アプリケーション] ページが表示されます。**ソース**ビュー ページの HTML 要素を確認できます。 デザイナーにはいくつかの <xref:System.Web.UI.WebControls.Content> コントロールのマークアップが表示されます。 各コントロールは、既定のアプリケーション マスター ページに定義されている <xref:System.Web.UI.WebControls.ContentPlaceHolder> コントロールにマップされます。

## <a name="designing-the-layout-of-the-application-page"></a>アプリケーション ページのレイアウトのデザイン

アプリケーション ページ項目を使用すると、デザイナーで ASP.NET コントロールをアプリケーション ページに追加できます。 このデザイナーは、Visual Web Developer で使用するデザイナーと同じです。 ラベル、ラジオ ボタンの一覧と、テーブルを追加、**ソース**デザイナーの表示し、標準の ASP.NET ページをデザインするときと同じようにプロパティを設定します。

1. メニュー バーで **[表示]**、**[ツールボックス]** の順に選択します。

2. 標準的なノードで、**ツールボックス**、次の手順のいずれかを実行します。

    - ショートカット メニューを開き、**ラベル**項目を選択**コピー**、下にある行のショートカット メニューを開き、 **PlaceHolderMain**コンテンツ コントロールをデザイナーで、し、選択**貼り付け**です。

    - ドラッグ、**ラベル**項目を**ツールボックス**の本文に、 **PlaceHolderMain**コンテンツ コントロールです。

3. 前の手順を繰り返して追加、 **DropDownList**項目と**テーブル**項目を**PlaceHolderMain**コンテンツ コントロールです。

4. デザイナーでの値を変更、`Text`するラベル コントロールの属性**Show All Items**です。

5. デザイナーで、`<asp:DropDownList>` 要素を次の XML に置き換えます。

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handling-the-events-of-controls-on-the-page"></a>ページ上のコントロールのイベントを処理する

ASP.NET ページと同様に、アプリケーション ページのコントロールを処理します。 この手順では、ドロップダウン リストの `SelectedIndexChanged` イベントを処理します。

1. **ビュー** ] メニューの [選択**コード**です。

     コード エディターでアプリケーション ページ コード ファイルが開きます。

2. `SearchItems` クラスに次のメソッドを追加します。 このコードでは、このチュートリアルでこれから作成するメソッドを呼び出して、<xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> の <xref:System.Web.UI.WebControls.DropDownList> イベントを処理します。

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. アプリケーション ページ コード ファイルの先頭に次のステートメントを追加します。

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. `SearchItems` クラスに次のメソッドを追加します。 このメソッドでは、サーバー ファーム上のすべてのサイトについて反復処理を行い、現在のユーザーが作成または変更した項目を検索します。

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. `SearchItems` クラスに次のメソッドを追加します。 このメソッドでは、現在のユーザーが作成または変更した項目をテーブルに表示します。

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="testing-the-application-page"></a>アプリケーション ページのテスト

プロジェクトを実行すると、SharePoint サイトが開き、アプリケーション ページが表示されます。

1. **ソリューション エクスプ ローラー**、アプリケーション ページのショートカット メニューを開きを選択し、**スタートアップ アイテムとして設定**です。

2. F5 キーを押します。

     SharePoint サイトが開きます。

3. [アプリケーション] ページで、選択、**自分で更新**オプション。

     アプリケーション ページが更新され、サーバー ファーム上のすべてのサイトで自分が変更したすべての項目が表示されます。

4. [アプリケーション] ページで、次のように選択します。**自分で作成した**一覧にします。

     アプリケーション ページが更新され、サーバー ファーム上のすべてのサイトで自分が作成したすべての項目が表示されます。

## <a name="next-ateps"></a>[次へ] ateps

SharePoint アプリケーション ページの詳細については、次を参照してください。 [for SharePoint アプリケーション ページを作成する](../sharepoint/creating-application-pages-for-sharepoint.md)です。

Visual Web Designer を使用して、SharePoint ページの内容をデザインする方法の詳細については、以下のトピックを参照してください。

- [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)です。

- [Web パーツまたはアプリケーション ページの再利用可能なコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)です。

## <a name="see-also"></a>関連項目

[方法: アプリケーション ページを作成する](../sharepoint/how-to-create-an-application-page.md)  
[アプリケーション _layouts ページ型](http://go.microsoft.com/fwlink/?LinkID=169274)
