---
title: 'チュートリアル: 基本サイト定義プロジェクトの作成 |Microsoft ドキュメント'
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
ms.openlocfilehash: 77c8d2151380c48b80b53ec3f0ef671daa92dbaa
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>チュートリアル: 基本サイト定義プロジェクトの作成
  このチュートリアルでは、一部のコントロールに視覚的 Web パーツを含む基本的なサイト定義を作成する方法を示します。 わかりやすくは、作成した視覚的 Web パーツは、いくつかのコントロールのみがします。 ただし、多くの機能を含むより高度な SharePoint サイト定義を作成できます。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   使用してサイト定義を作成する、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]プロジェクト テンプレート。  
  
-   SharePoint のサイト定義を使用して、SharePoint サイトを作成しています。  
  
-   ソリューションに視覚的 Web パーツを追加します。  
  
-   新しい視覚的 Web パーツを追加して、サイトの default.aspx ページをカスタマイズします。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。 詳細については、SharePoint ソリューションの開発要件を参照してください。  
  
-   Visual Studio  
  
## <a name="creating-a-site-definition-solution"></a>サイト定義ソリューションを作成します。  
 最初に、サイト定義プロジェクトの作成で[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
#### <a name="to-create-a-site-definition-project"></a>サイト定義プロジェクトを作成するには  
  
1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]** の順にクリックします。 IDE は、Visual Basic 開発設定を使用して、メニュー バーでに設定されている場合は、選択**ファイル**、**新しいプロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  展開、 **Visual c#** ノードまたは**Visual Basic**ノード、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
3.  **テンプレート**一覧で、選択、 **SharePoint 2010 プロジェクト**テンプレート。  
  
4.  **名前**ボックスに、入力**TestSiteDef**を選択し、 **OK**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
5.  **デバッグのサイトとセキュリティ レベルを指定して**ページで、サイト定義をデバッグする SharePoint サイトの URL を入力するか、既定の場所を使用して (http://*システム名*/)。  
  
6.  **この SharePoint ソリューションの信頼レベルは何ですか?** セクションで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックします。  
  
     すべてのサイト定義プロジェクトはファーム ソリューションとして配置する必要があります。 サンド ボックス ソリューションとファーム ソリューションの詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)です。  
  
7.  選択、**完了**ボタンをクリックします。  
  
     プロジェクトが表示されます**ソリューション エクスプ ローラー**です。  
  
8.  **ソリューション エクスプ ローラー**、プロジェクト ノードを選択し、次に、メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
9. いずれかで**Visual c#** または**Visual Basic**、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
10. **テンプレート** ウィンドウで、選択、**サイト定義**のままにして、テンプレート、**名前**として**SiteDefinition1**、をクリックして**追加**ボタンをクリックします。  
  
## <a name="create-a-visual-web-part"></a>視覚的 Web パーツを作成します。  
 次に、サイト定義のメイン ページに表示する視覚的 Web パーツを作成します。  
  
#### <a name="to-create-a-visual-web-part"></a>視覚的 Web パーツを作成するには  
  
1.  **ソリューション エクスプ ローラー**、選択、 **すべてのファイル**ボタンをクリックします。  
  
2.  選択、 **SiteDefinition1**プロジェクト ノード、およびその後、メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
     **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
3.  展開、 **Visual c#** ノードまたは**Visual Basic**ノード、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
4.  テンプレートの一覧で選択、**視覚的 Web パーツ**テンプレート、既定値は、VisualWebPart1 の名前を指定しを選択し、保持、**追加**ボタンをクリックします。  
  
     VisualWebPart1.ascx ファイルが開きます。  
  
5.  VisualWebPart1.ascx の下部には、3 つのコントロールをフォームに追加するのには、次のマークアップを追加します。 テキスト ボックス、ボタン、およびラベル。  
  
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
  
6.  VisualWebPart1.ascx、下にある VisualWebPart1.ascx.cs ファイルを開きます (の[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) または VisualWebPart1.ascx.vb (の[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])、し、次のコードを追加します。  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     このコードは、web パーツのボタン クリックの機能を追加します。  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>既定の ASPX ページを視覚的 Web パーツを追加します。  
 次に、サイト定義の既定の ASPX ページを視覚的 Web パーツを追加します。  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>既定の ASPX ページを視覚的 Web パーツを追加するには  
  
1.  Default.aspx ページを開き、下にある次の行を追加、`WebPartPages`タグ。  
  
    ```aspx-csharp  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     この行では、Web パーツでそのコード名 MyWebPartControls を関連付けます。 *Namespace*パラメーター VisualWebPart1.ascx コード ファイルで使用されている名前空間に一致します。  
  
2.  後に、`</asp:Content>`要素全体を置き換える`ContentPlaceHolderId="PlaceHolderMain"`セクションとその内容を次のコード。  
  
    ```aspx-csharp  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     このコードでは、先ほど作成した視覚的 Web パーツへの参照を作成します。  
  
3.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SiteDefinition1**  ノードを選択し**スタートアップ アイテムとして設定**です。  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>サイト定義ソリューションを配置して実行する  
 次に、SharePoint にプロジェクトを配置し、プロジェクトを実行します。  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>サイト定義を配置して実行するには  
  
-   メニュー バーで、次のように選択します。**ビルド**、**展開 TestSiteDef**です。  
  
-   F5 キーを押します。  
  
     Visual Studio で、コードをコンパイル、その機能が追加されて、SharePoint ソリューション (WSP) ファイルでは、すべてのファイルにパッケージ化、および WSP ファイルの SharePoint サーバーに展開します。 SharePoint では、し、ファイルをインストールしの機能をアクティブにします。  
  
## <a name="create-a-site-based-on-the-site-definition"></a>サイト定義に基づくサイトを作成します。  
 次に、新しいサイト定義を使用して、サイトを作成します。  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>サイト定義を使用してサイトを作成するには  
  
1.  SharePoint サイトでは、新しい SharePoint サイト ページが表示されます。  
  
2.  **タイトルと説明**セクションで、入力**新しいマイサイト**タイトルと、サイトの説明。  
  
3.  **Web サイトのアドレス**セクションで、入力**mynewsite**で、 **URL 名**ボックス。  
  
4.  **テンプレート**セクションで、選択、 **SharePoint のカスタマイズ**タブです。  
  
5.  **テンプレートを選択して**一覧で、選択**SiteDefinition1**です。  
  
6.  既定値、その他の設定のままにし、、**作成**ボタンをクリックします。  
  
     新しいサイトが表示されます。  
  
## <a name="test-the-new-site"></a>新しいサイトをテストします。  
 次に、正常に動作するかどうかを確認する、新しいサイトをテストします。  
  
#### <a name="to-test-the-new-site"></a>新しいサイトをテストするには  
  
-   既定の ASPX ページで、テキストを入力し、、**ラベル テキストの変更**テキスト ボックスの横にあるボタンをクリックします。  
  
     ボタンの右側にあるラベルのテキストが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [方法: イベント レシーバーを作成します。](../sharepoint/how-to-create-an-event-receiver.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  