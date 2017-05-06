---
title: "チュートリアル: SharePoint アプリケーション ページの作成"
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
  - "アプリケーション ページ [Visual Studio での SharePoint 開発]、開発"
  - "アプリケーション ページ [Visual Studio での SharePoint 開発]、作成"
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# チュートリアル: SharePoint アプリケーション ページの作成
  アプリケーション ページとは、特殊なフォームの ASP.NET ページです。  アプリケーション ページには、SharePoint のマスター ページとマージされるコンテンツが含まれます。  詳細については、「[SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)」を参照してください。  
  
 このチュートリアルでは、アプリケーション ページを作成し、そのページをローカル SharePoint サイトを使ってデバッグする方法を説明します。  このページには、サーバー ファーム上のあらゆるサイトで、各ユーザーが作成または変更したすべての項目が表示されます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   SharePoint プロジェクトを作成する  
  
-   SharePoint プロジェクトにアプリケーション ページを追加する  
  
-   アプリケーション ページに ASP.NET コントロールを追加する  
  
-   ASP.NET コントロールに分離コードを追加する  
  
-   アプリケーション ページをテストする  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows と SharePoint。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] \(Visual Studio Ultimate または Visual Studio Premium\)。  
  
## SharePoint プロジェクトを作成する  
 まず、**空の SharePoint プロジェクト**を作成します。  後で、このプロジェクトに**アプリケーション ページ**項目を追加します。  
  
#### SharePoint プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスを開き、使用する言語の **\[Office SharePoint\]** ノードを展開して、**\[SharePoint ソリューション\]** ノードを選択します。  
  
3.  **\[Visual Studio にインストールされたテンプレート\]** ペインで **\[SharePoint 2010 \- 空のプロジェクト\]** を選択します。  プロジェクトに「MySharePointProject」という名前を付け、**\[OK\]** をクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  このウィザードを使用すると、プロジェクトのデバッグに使用するサイトや、ソリューションの信頼レベルを選択できます。  
  
4.  **\[ファーム ソリューションとして配置する\]** をクリックします。ローカル SharePoint サイトの構成は既定値のままで、**\[完了\]** をクリックします。  
  
## アプリケーション ページを作成する  
 アプリケーション ページを作成するには、プロジェクトに**アプリケーション ページ**項目を追加します。  
  
#### アプリケーション ページを作成するには  
  
1.  **ソリューション エクスプローラー**で、**MySharePointProject** プロジェクトを選択します。  
  
2.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[アプリケーション ページ \(ファーム ソリューションのみ\)\]** テンプレートを選択します。  
  
4.  このページに「SearchItems」という名前を付け、**\[追加\]** をクリックします。  
  
     Visual Web Developer デザイナーの**ソース** ビューにアプリケーション ページが表示されます。このビューでは、対象ページの HTML 要素を確認できます。  デザイナーにはいくつかの <xref:System.Web.UI.WebControls.Content> コントロールのマークアップが表示されます。  各コントロールは、既定のアプリケーション マスター ページに定義されている <xref:System.Web.UI.WebControls.ContentPlaceHolder> コントロールにマップされます。  
  
## アプリケーション ページのレイアウトのデザイン  
 アプリケーション ページ項目を使用すると、デザイナーで ASP.NET コントロールをアプリケーション ページに追加できます。  このデザイナーは、Visual Web Developer で使用するデザイナーと同じです。  ラベル、オプション ボタン リスト、およびテーブルをデザイナーの**ソース** ビューに追加し、標準的な ASP.NET ページをデザインする場合と同様にプロパティを設定します。  
  
 Visual Web Developer のデザイナーの使用方法については、「[Visual Studio Web Development Content Map](http://msdn.microsoft.com/ja-jp/9c31f93b-c8fb-4599-9b14-6194ec8c7539)」を参照してください。  
  
#### アプリケーション ページのレイアウトをデザインするには  
  
1.  メニュー バーで **\[表示\]**、**\[ツールボックス\]** の順にクリックします。  
  
2.  **ツールボックス**の \[標準\] ノードで、次のいずれかの手順に従います。  
  
    -   **\[Label\]**項目のショートカット メニューを開き、**\[コピー\]** を選択します。デザイナーで、**PlaceHolderMain** コンテンツ コントロールの下にある行のショートカット メニューを開き、**\[貼り付け\]**を選択します。  
  
    -   **ツールボックス**の **\[Label\]** 項目を、**PlaceHolderMain** コンテンツ コントロールの本体までドラッグします。  
  
3.  上記と同じ手順で、**\[DropDownList\]** 項目と **\[Table\]** 項目を **PlaceHolderMain** コンテンツ コントロールに追加します。  
  
4.  デザイナーで、ラベル コントロールの `Text` 属性の値を「Show All Items」に変更します。  
  
5.  デザイナーで、`<asp:DropDownList>` 要素を次の XML に置き換えます。  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## ページ上のコントロールのイベントを処理する  
 ASP.NET ページと同様に、アプリケーション ページのコントロールを処理します。  この手順では、ドロップダウン リストの `SelectedIndexChanged` イベントを処理します。  
  
#### ページ上のコントロールのイベントを処理するには  
  
1.  **\[表示\]** メニューの **\[コード\]** を選択します。  
  
     コード エディターでアプリケーション ページ コード ファイルが開きます。  
  
2.  `SearchItems` クラスに次のメソッドを追加します。  このコードでは、このチュートリアルでこれから作成するメソッドを呼び出して、<xref:System.Web.UI.WebControls.DropDownList> の <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> イベントを処理します。  
  
     [!code-csharp[SP_ApplicationPage#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]
     [!code-vb[SP_ApplicationPage#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]  
  
3.  アプリケーション ページ コード ファイルの先頭に次のステートメントを追加します。  
  
     [!code-csharp[SP_ApplicationPage#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]
     [!code-vb[SP_ApplicationPage#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]  
  
4.  `SearchItems` クラスに次のメソッドを追加します。  このメソッドでは、サーバー ファーム上のすべてのサイトについて反復処理を行い、現在のユーザーが作成または変更した項目を検索します。  
  
     [!code-csharp[SP_ApplicationPage#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]
     [!code-vb[SP_ApplicationPage#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]  
  
5.  `SearchItems` クラスに次のメソッドを追加します。  このメソッドでは、現在のユーザーが作成または変更した項目をテーブルに表示します。  
  
     [!code-csharp[SP_ApplicationPage#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]
     [!code-vb[SP_ApplicationPage#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]  
  
## アプリケーション ページのテスト  
 プロジェクトを実行すると、SharePoint サイトが開き、アプリケーション ページが表示されます。  
  
#### アプリケーション ページをテストするには  
  
1.  **ソリューション エクスプローラー**で、アプリケーション ページのショートカット メニューを開き、**\[スタートアップ アイテムとして設定\]** を選択します。  
  
2.  F5 キーを押します。  
  
     SharePoint サイトが開きます。  
  
3.  アプリケーション ページで **\[自分が更新者\]** を選択します。  
  
     アプリケーション ページが更新され、サーバー ファーム上のすべてのサイトで自分が変更したすべての項目が表示されます。  
  
4.  アプリケーション ページの一覧で **\[現在のユーザーが作成\]** を選択します。  
  
     アプリケーション ページが更新され、サーバー ファーム上のすべてのサイトで自分が作成したすべての項目が表示されます。  
  
## 次の手順  
 SharePoint のアプリケーション ページの詳細については、「[SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)」を参照してください。  
  
 Visual Web Designer を使用して、SharePoint ページの内容をデザインする方法の詳細については、以下のトピックを参照してください。  
  
-   [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## 参照  
 [方法: アプリケーション ページを作成する](../sharepoint/how-to-create-an-application-page.md)   
 [Application \_layouts Page Type \(アプリケーション レイアウト ページの種類\)](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  