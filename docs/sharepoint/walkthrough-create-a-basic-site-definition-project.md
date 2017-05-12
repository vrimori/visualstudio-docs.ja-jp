---
title: "チュートリアル: 基本サイト定義プロジェクトの作成"
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
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# チュートリアル: 基本サイト定義プロジェクトの作成
  このチュートリアルでは、可視 Web パーツとそこに配置されたいくつかのコントロールを含んだ基本的なサイト定義を作成する方法について説明します。  わかりやすく説明するために、ここで作成する可視 Web パーツには数個のコントロールしか配置されていないことにします。  実用するために、より多機能な洗練された SharePoint サイト定義を作成することはできます。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクト テンプレートを使用してサイト定義を作成する。  
  
-   SharePoint でサイト定義を使用して SharePoint サイトを作成する。  
  
-   可視 Web パーツをソリューションに追加する。  
  
-   サイトの default.aspx ページに新しい可視 Web パーツを追加してカスタマイズする。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。  詳細については、「SharePoint ソリューションの開発要件」を参照してください。  
  
-   Visual Studio  
  
## サイト定義ソリューションの作成  
 まず、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] でサイト定義プロジェクトを作成します。  
  
#### サイト定義プロジェクトを作成するには  
  
1.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  Visual Basic 開発設定を選択し、メニュー バーで使用する IDE が設定されている場合、**\[新しいプロジェクト\]\[ファイル\]** をクリックします。  
  
     \[新しいプロジェクト\] ダイアログ ボックスが表示されます。  
  
2.  **\[Visual C\#\]** ノードまたは **\[Visual Basic\]** ノードを展開し、**\[SharePoint\]** ノードを展開し、**2010** ノードを選択します。  
  
3.  **\[テンプレート\]** の一覧で、**\[SharePoint 2010 プロジェクト\]** テンプレートを選択します。  
  
4.  **\[名前\]** ボックスで、TestSiteDef を入力し、**\[OK\]** ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
5.  **\[デバッグのサイトとセキュリティ レベルの指定\]** ページで、サイト定義をデバッグすると入力するか、既定の場所 \(http:\/\/*System Name*\/\) を使用して、SharePoint サイトの URL です。  
  
6.  **\[この SharePoint ソリューションの信頼レベル\]** セクションで **\[ファーム ソリューションとして配置する\]** を選択します。  
  
     サイト定義プロジェクトはすべてファーム ソリューションとして配置する必要があります。  サンドボックス ソリューションとファーム ソリューションの違いの詳細については、「[サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)」を参照してください。  
  
7.  **\[完了\]** をクリックします。  
  
     **ソリューション エクスプローラー**にプロジェクトが表示されます。  
  
8.  次に **\[ソリューション エクスプローラー\]** で、プロジェクト ノードを選択し、メニュー バーで、**\[プロジェクト\]** をクリックします、**\[新しいアイテムの追加\]** を選択します。  
  
9. **\[Visual C\#\]** または **\[Visual Basic\]** で、**\[SharePoint\]** ノードを展開し、**2010** ノードを選択します。  
  
10. **\[テンプレート\]** のペインで、**\[サイト定義\]** テンプレートを選択し、**\[SiteDefinition1\]** として **\[名前\]** のままにして、次へ **\[追加\]** ボタンをクリックします。  
  
## 可視 Web パーツの作成  
 次に、サイト定義のメイン ページに表示する、可視 Web パーツを作成します。  
  
#### 可視 Web パーツを作成するには  
  
1.  **\[ソリューション エクスプローラー\]** で、**\[すべてのファイルを表示\]** ボタンをクリックします。  
  
2.  次に **\[SiteDefinition1\]** のプロジェクト ノードを選択し、メニュー バーで選択し、**\[新しいアイテムの追加\]\[プロジェクト\]** をクリックします。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
3.  **\[Visual C\#\]** ノードまたは **\[Visual Basic\]** ノードを展開し、**\[SharePoint\]** ノードを展開し、**2010** ノードを選択します。  
  
4.  テンプレートの一覧で、**\[視覚的 Web パーツ\]** テンプレートを選択し、既定の名前 VisualWebPart1 を保持し、次へ **\[追加\]** ボタンをクリックします。  
  
     VisualWebPart1.ascx ファイルが開きます。  
  
5.  VisualWebPart1.ascx で、フォームの 3 種類のコントロールを追加するには、次のマークアップを追加する: テキスト ボックス、ボタン、ラベル:  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  VisualWebPart1.ascx で、VisualWebPart1.ascx.cs ファイル \([!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]の場合\) または VisualWebPart1.ascx.vb \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]の場合\) を開き、次のコードを追加する:  
  
     [!code-csharp[SP_SimpleSiteDef#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_simplesitedef/cs/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_SimpleSiteDef#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_simplesitedef/vb/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
     このコードによって、Web パーツのボタン クリック用の機能が追加されます。  
  
## 既定の ASPX ページへの可視 Web パーツの追加  
 次に、可視 Web パーツをサイト定義の既定の ASPX ページに追加します。  
  
#### 可視 Web パーツを既定の ASPX ページに追加するには  
  
1.  default.aspx ページを開き、`WebPartPages` タグの下に次の行を追加する:  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     このコードによって、Web パーツとそのコードに対し、MyWebPartControls という名前が関連付けられます。  *Namespace* パラメーターは VisualWebPart1.ascx コード ファイルで使用される名前空間と一致します。  
  
2.  `</asp:Content>` 要素の後に、次のコードに `ContentPlaceHolderId="PlaceHolderMain"` セクション全体とその内容を置換する:  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     先ほど作成した可視 Web パーツへの参照がこのコードによって作成されます。  
  
3.  **\[ソリューション エクスプローラー\]** で、**\[SiteDefinition1\]** ノードのショートカット メニューを開き、**\[スタートアップ アイテムとして設定\(S\)\]** をクリックします。  
  
## サイト定義ソリューションを配置して実行する  
 次に、プロジェクトを SharePoint に配置した後にプロジェクトを実行します。  
  
#### サイト定義を配置して実行するには  
  
-   メニュー バーで、**\[TestSiteDef を配置します。\]\[ビルド\]** をクリックします。  
  
-   F5 キーを押します。  
  
     Visual Studio には、SharePoint ソリューション \(WSP\) ファイルにコードを追加して、機能をパッケージ化し、すべてのファイルが SharePoint Server に配置して WSP ファイルをコンパイルします。  さらに、SharePoint によってファイルがインストールされて、フィーチャーがアクティブ化されます。  
  
## サイト定義に基づくサイトの作成  
 次に、新しいサイト定義を使用してサイトを作成します。  
  
#### サイト定義を使用してサイトを作成するには  
  
1.  SharePoint サイトでは、\[新しい SharePoint サイト\] ページが表示されます。  
  
2.  **\[タイトルと説明\]** セクションで、サイトのタイトルと説明に「My New Site」と入力します。  
  
3.  **\[Web サイトのアドレス\]** セクションの \[URL 名\] ボックスに「**mynewsite**」と入力します。  
  
4.  **\[テンプレート\]** セクションで、**\[SharePoint のカスタマイズ\]** タブをクリックします。  
  
5.  **\[テンプレートの選択\]** の一覧で、**\[SiteDefinition1\]** をクリックします。  
  
6.  そのほかの設定を既定値のままとし、**\[作成\]** ボタンをクリックします。  
  
     新しいサイトが表示されます。  
  
## 新しいサイトのテスト  
 次に、適切に動作するかどうかを検証するために、新しいサイトをテストします。  
  
#### 新しいサイトをテストするには  
  
-   既定の ASPX ページにテキストを入力し、テキスト ボックスの横に **\[ラベルのテキストを変更します。\]** ボタンをクリックします。  
  
     テキストはボタンの右側のラベルに表示されます。  
  
## 参照  
 [方法: イベント レシーバーを作成する](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  