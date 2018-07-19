---
title: 'チュートリアル: 基本的なサイト定義プロジェクトの作成 |Microsoft Docs'
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dee03e2cd7b1c22faf5f1b06ec5efe763bad1387
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119826"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>チュートリアル: 基本的なサイト定義プロジェクトを作成します。
  このチュートリアルでは、一部のコントロールに視覚的 Web パーツを含む基本的なサイト定義を作成する方法を示します。 わかりやすくする、作成した視覚的 Web パーツにはいくつかのコントロールがあります。 ただし、多くの機能を含むより高度な SharePoint サイト定義を作成できます。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   使用してサイト定義を作成する、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]プロジェクト テンプレート。  
  
-   SharePoint のサイト定義を使用して SharePoint サイトを作成します。  
  
-   ソリューションに視覚的 Web パーツを追加します。  
  
-   新しいビジュアル Web パーツを追加して、サイトの default.aspx ページをカスタマイズします。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>前提条件  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。 詳細については、SharePoint ソリューションを開発するための要件を参照してください。  
  
-   Visual Studio  
  
## <a name="create-a-site-definition-solution"></a>サイト定義ソリューションを作成します。
 まずでサイト定義プロジェクト作成[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
#### <a name="to-create-a-site-definition-project"></a>サイト定義プロジェクトを作成するには  
  
1.  メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。 お使いの IDE が Visual Basic 開発設定を使用して、メニュー バーに設定されている場合は、選択**ファイル** > **新しいプロジェクト**します。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  展開、 **Visual c#** ノードまたは**Visual Basic**ノード、展開、 **SharePoint**ノードを選択し、 **2010**ノード。  
  
3.  **テンプレート**一覧で、選択、 **SharePoint 2010 プロジェクト**テンプレート。  
  
4.  **名前**ボックスに、入力**TestSiteDef**、選択し、 **OK**ボタン。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
5.  **デバッグのサイトとセキュリティのレベルを指定**ページで、サイト定義をデバッグする SharePoint サイトの URL を入力するか、既定の場所を使用して (http://*システム名*/)。  
  
6.  **この SharePoint ソリューションの信頼レベルとは何ですか?** セクションで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックします。  
  
     すべてのサイト定義プロジェクトはファーム ソリューションとして配置する必要があります。 サンド ボックス ソリューションとファーム ソリューションの詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)します。  
  
7.  選択、**完了**ボタンをクリックします。  
  
     プロジェクトが表示されます**ソリューション エクスプ ローラー**します。  
  
8.  **ソリューション エクスプ ローラー**をプロジェクト ノードを選択し、メニュー バーで、次のように選択します。**プロジェクト** > **新しい項目の追加**します。  
  
9. いずれかで**Visual c#** または**Visual Basic**、展開、 **SharePoint**ノードを選択し、 **2010**ノード。  
  
10. **テンプレート**ウィンドウで、選択、**サイト定義**のままに、テンプレート、**名前**として**SiteDefinition1**、を選択し**追加**ボタンをクリックします。  
  
## <a name="create-a-visual-web-part"></a>視覚的 web パーツを作成します。
 次に、サイト定義のメイン ページに表示する視覚的 Web パーツを作成します。  
  
#### <a name="to-create-a-visual-web-part"></a>視覚的 web パーツを作成するには
  
1.  **ソリューション エクスプ ローラー**、選択、 **すべてのファイル**ボタンをクリックします。  
  
2.  選択、 **SiteDefinition1**プロジェクト ノード、およびその後、メニュー バーで、次のように選択します。**プロジェクト** > **新しい項目の追加**します。  
  
     **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
3.  展開、 **Visual c#** ノードまたは**Visual Basic**ノード、展開、 **SharePoint**ノードを選択し、 **2010**ノード。  
  
4.  テンプレートの一覧で選択、**視覚的 Web パーツ**テンプレート、既定の名前を VisualWebPart1 をクリックしてください、**追加**ボタンをクリックします。  
  
     *VisualWebPart1.ascx*ファイルが開きます。  
  
5.  下部にある*VisualWebPart1.ascx*、3 つのコントロールをフォームに追加するのには、次のマークアップを追加します。 テキスト ボックス、ボタン、およびラベル。  
  
    ```aspx-csharp  
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
  
6.  *VisualWebPart1.ascx*、オープン、 *VisualWebPart1.ascx.cs*ファイル (の[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) または*VisualWebPart1.ascx.vb* (の[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])、しを追加次のコードでは:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     このコードは、web パーツのボタン クリックの機能を追加します。  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>既定の ASPX ページを視覚的 web パーツを追加します。
 次に、サイト定義の既定の ASPX ページを視覚的 Web パーツを追加します。  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>既定の ASPX ページを視覚的 web パーツを追加するには
  
1.  Default.aspx ページを開き、下にある次の行を追加、`WebPartPages`タグ。  
  
    ```aspx-csharp  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     この行では、Web パーツでそのコード名 MyWebPartControls を関連付けます。 *Namespace*パラメーターで使用される名前空間に一致、 *VisualWebPart1.ascx*コード ファイル。  
  
2.  後に、`</asp:Content>`要素全体を置き換える`ContentPlaceHolderId="PlaceHolderMain"`セクションとその内容を次のコード。  
  
    ```aspx-csharp  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     このコードでは、先ほど作成した視覚的 Web パーツへの参照を作成します。  
  
3.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SiteDefinition1**ノードを選び、**スタートアップ アイテムとして設定**します。  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>展開してサイト定義ソリューションの実行
 次に、プロジェクト、SharePoint をデプロイして、プロジェクトを実行します。  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>サイト定義を配置して実行するには  
  
-   メニュー バーで、**ビルド** > **デプロイ TestSiteDef**します。  
  
-   **F5** キーを押します。  
  
     Visual Studio では、コードをコンパイル、その機能を追加します。 SharePoint ソリューション (WSP) ファイルでは、すべてのファイルにパッケージ化、WSP ファイルを SharePoint サーバーにデプロイします。 SharePoint では、し、ファイルをインストールし、機能をアクティブにします。  
  
## <a name="create-a-site-based-on-the-site-definition"></a>サイト定義に基づいてサイトを作成します。
 次に、新しいサイト定義を使用して、サイトを作成します。  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>サイト定義を使用してサイトを作成するには  
  
1.  SharePoint サイトでは、新しい SharePoint サイトのページが表示されます。  
  
2.  **タイトルと説明**セクションに、入力**新しい マイサイト**タイトルと、サイトの説明。  
  
3.  **Web サイトのアドレス**セクションに、入力**mynewsite**で、 **URL 名**ボックス。  
  
4.  **テンプレート**セクションで、選択、 **SharePoint のカスタマイズ**タブ。  
  
5.  **テンプレートを選択して**一覧で、選択**SiteDefinition1**します。  
  
6.  その既定値では、その他の設定のままにして、**作成**ボタンをクリックします。  
  
     新しいサイトが表示されます。  
  
## <a name="test-the-new-site"></a>新しいサイトをテストします。
 次に、正常に動作するかどうかを確認する新しいサイトをテストします。  
  
#### <a name="to-test-the-new-site"></a>新しいサイトをテストするには  
  
-   既定の ASPX ページで、テキストを入力し、、**ラベル テキストの変更**テキスト ボックスの横にあるボタンをクリックします。  
  
     ボタンの右側にあるラベルのテキストが表示されます。  
  
## <a name="see-also"></a>関連項目
 [方法: イベント レシーバーを作成](../sharepoint/how-to-create-an-event-receiver.md)   
 [SharePoint ソリューションを開発します。](../sharepoint/developing-sharepoint-solutions.md)  
  
