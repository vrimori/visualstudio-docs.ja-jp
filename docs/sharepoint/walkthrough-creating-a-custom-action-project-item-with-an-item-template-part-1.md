---
title: 'チュートリアル: 項目テンプレートを使用したカスタム動作プロジェクト項目の作成、パート 1 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8144723f68b9343c1c7d74f7a940aec569dd7969
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296126"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>チュートリアル: 項目テンプレート、第 1 部でのカスタム動作プロジェクト項目を作成します。
  Visual Studio の SharePoint プロジェクト システムは、プロジェクト項目の種類を独自に作成することによって拡張することができます。 このチュートリアルでは、SharePoint サイトのカスタム アクションを作成する SharePoint プロジェクトに追加できるプロジェクト項目を作成します。 カスタム アクションにメニュー項目の追加、**サイトの操作**SharePoint サイトのメニュー。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
- カスタム動作のための SharePoint プロジェクト項目の新しい種類を定義する Visual Studio 拡張機能の作成。 この新しいプロジェクト項目の種類では、次に示すいくつかのカスタム機能を実装します。  
  
  -   プロジェクト項目に関連したさまざまな追加タスク (Visual Studio でカスタム動作を作成するためのデザイナーを表示するなど) の開始点となるショートカット メニュー。  
  
  -   開発者がプロジェクト項目やそれを含んでいるプロジェクトの特定のプロパティを変更したときに実行されるコード。  
  
  -   プロジェクト項目の横に表示されるカスタム アイコン**ソリューション エクスプ ローラー**します。  
  
- 対応するプロジェクト項目用の Visual Studio 項目テンプレートを作成する。  
  
- プロジェクト項目テンプレートや拡張機能のアセンブリを配置するための Visual Studio Extension (VSIX) パッケージを構築する。  
  
- プロジェクト項目のデバッグとテストを行う。  
  
  これは、独立したチュートリアルです。 このチュートリアルを完了すると、項目テンプレートにウィザードを追加してプロジェクト項目を拡張できるようになります。 詳細については、次を参照してください。[チュートリアル: 項目テンプレート、第 2 部でのカスタム動作プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)です。  
  
> [!NOTE]  
>  サンプルをダウンロードする[Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities)ワークフローのカスタム アクティビティを作成する方法を示すです。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
- サポート対象エディションの Microsoft Windows、SharePoint、および Visual Studio。
  
- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 このチュートリアルでは、 **VSIX プロジェクト**sdk プロジェクト アイテムを配置するための VSIX パッケージを作成するテンプレート。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)します。  
  
  次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
- SharePoint のカスタム動作。 詳細については、次を参照してください。[カスタム アクション](http://go.microsoft.com/fwlink/?LinkId=177800)します。  
  
- Visual Studio の項目テンプレート。 詳細については、「[Creating Project and Item Templates](/visualstudio/ide/creating-project-and-item-templates)」 (プロジェクトと項目テンプレートの作成) をご覧ください。  
  
## <a name="create-the-projects"></a>プロジェクトを作成します。
 このチュートリアルを実行するには、3 つのプロジェクトを作成する必要があります。  
  
- VSIX プロジェクト。 このプロジェクトは、SharePoint プロジェクト項目を配置するための VSIX パッケージを作成します。  
  
- 項目テンプレート プロジェクト。 このプロジェクトは、SharePoint プロジェクト項目を SharePoint プロジェクトに追加するために使用できる項目テンプレートを作成します。  
  
- クラス ライブラリ プロジェクト。 このプロジェクトは、SharePoint プロジェクト項目の動作を定義する Visual Studio 拡張機能を実装します。  
  
  この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。  
  
3.  上部にある一覧で、**新しいプロジェクト** ダイアログ ボックスに、必ず **.NET Framework 4.5**が選択されています。  
  
4.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** または**Visual Basic**ノードを選択し、**機能拡張**ノード。  
  
    > [!NOTE]  
    >  **Extensibility**ノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
5.  選択、 **VSIX プロジェクト**テンプレート。  
  
6.  **名前**ボックスに、入力**CustomActionProjectItem**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **CustomActionProjectItem**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
#### <a name="to-create-the-item-template-project"></a>項目テンプレート プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。  
  
2.  上部にある一覧で、**新しいプロジェクト** ダイアログ ボックスに、必ず **.NET Framework 4.5**が選択されています。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** または**Visual Basic**ノードを選択し、**機能拡張**ノード。  
  
4.  プロジェクト テンプレートの一覧で選択、 **c# 項目テンプレート**または**Visual Basic 項目テンプレート**テンプレート。  
  
5.  **名前**ボックスに、入力**ItemTemplate**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **ItemTemplate**プロジェクトがソリューションにします。  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。  
  
2.  上部にある一覧で、**新しいプロジェクト** ダイアログ ボックスに、必ず **.NET Framework 4.5**が選択されています。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** または**Visual Basic** 、ノードの選択、 **Windows**ノード、を選択し**クラス ライブラリ**プロジェクト テンプレート。  
  
4.  **名前**ボックスに、入力**ProjectItemDefinition**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **ProjectItemDefinition**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configure-the-extension-project"></a>拡張機能プロジェクトを構成します。
 SharePoint プロジェクト項目の種類を定義するためのコードを記述する前に、コード ファイルおよびアセンブリ参照を拡張機能プロジェクトに追加しておく必要があります。  
  
#### <a name="to-configure-the-project"></a>プロジェクトを構成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProjectItemDefinition**プロジェクトで、選択**追加**を選択し、**新しい項目の**します。  
  
2.  プロジェクト項目の一覧で選択**コード ファイル**します。  
  
3.  **名前**ボックスに、名前を入力**CustomAction**と適切なファイル名拡張子を選び、**追加**ボタンをクリックします。  
  
4.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProjectItemDefinition**プロジェクトを選び、**参照の追加**します。  
  
5.  **参照マネージャー - ProjectItemDefinition**  ダイアログ ボックスで、選択、**アセンブリ**ノードを選択し、 **Framework**ノード。  
  
6.  次の各アセンブリの横にあるチェック ボックスをオンにします。  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  選択、**拡張機能**ノードが、Microsoft.VisualStudio.Sharepoint アセンブリの横にあるチェック ボックスを選択し、、 **OK**ボタン。  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>新しい SharePoint プロジェクト項目の種類を定義します。
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスを実装するクラスを作成して、新しいプロジェクト項目の種類の動作を定義します。 このインターフェイスは、新しい種類のプロジェクト項目を定義するたびに必ず実装します。  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>新しい SharePoint プロジェクト項目の種類を定義するには  
  
1.  ProjectItemDefinition プロジェクトで、CustomAction コード ファイルを開きます。  
  
2.  このファイル内のコードを次のコードに置き換えます。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]  
  
## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>ソリューション エクスプ ローラーでプロジェクト項目のアイコンを作成します。
 カスタム SharePoint プロジェクト項目を作成した場合、そのプロジェクト項目にはイメージ (アイコンまたはビットマップ) を関連付けることができます。 プロジェクト項目の横にあるこの画像が表示されます**ソリューション エクスプ ローラー**します。  
  
 次の手順では、プロジェクト項目のアイコンを実際に作成し、拡張機能のアセンブリに埋め込みます。 このアイコンは、先ほど作成した <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> クラスの `CustomActionProjectItemTypeProvider` から参照されます。  
  
#### <a name="to-create-a-custom-icon-for-the-project-item"></a>プロジェクト項目のカスタム アイコンを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProjectItemDefinition**プロジェクトで、選択**追加**を選び、**新しい項目.**.  
  
2.  プロジェクト項目の一覧で選択、**アイコン ファイル**項目。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで選択する必要があります、**全般**を表示するノード、**アイコン ファイル**項目。  
  
3.  **名前**ボックスに、入力**CustomAction_SolutionExplorer.ico**、選択し、**追加**ボタンをクリックします。  
  
     新しいアイコンが表示、**イメージ エディター**します。  
  
4.  認識しやすいデザインとなるよう 16x16 版のアイコン ファイルを編集し、アイコン ファイルを保存します。  
  
5.  **ソリューション エクスプ ローラー**、選択**CustomAction_SolutionExplorer.ico**します。  
  
6.  **プロパティ**ウィンドウで、横にある矢印を選択、**ビルド アクション**プロパティ。  
  
7.  表示される一覧で選択**埋め込まれたリソース**します。  
  
## <a name="checkpoint"></a>チェックポイント  
 この段階で、プロジェクト項目に必要なすべてのコードがプロジェクトに揃ったことになります。 エラーが発生することなくプロジェクトをコンパイルできるかどうか、プロジェクトをビルドして確認してください。  
  
#### <a name="to-build-your-project"></a>プロジェクトをビルドするには  
  
1.  ショートカット メニューを開き、 **ProjectItemDefinition**プロジェクト**ビルド**します。  
  
## <a name="create-a-visual-studio-item-template"></a>Visual Studio 項目テンプレートを作成します。
 自分が定義したプロジェクト項目を他の開発者が使用できるようにするには、プロジェクト テンプレートまたは項目テンプレートを作成します。 Visual Studio で新しいプロジェクトを作成する際または既存のプロジェクトに項目を追加する際、開発者は、そのテンプレートを使用して、プロジェクト項目のインスタンスを作成します。 このチュートリアルでは、ItemTemplate プロジェクトを使用してプロジェクト項目を構成します。  
  
#### <a name="to-create-the-item-template"></a>項目テンプレートを作成するには  
  
1.  Class1 コード ファイルを ItemTemplate プロジェクトから削除します。  
  
2.  ItemTemplate プロジェクトで開き、 *ItemTemplate.vstemplate*ファイル。  
  
3.  ファイルの内容を次の XML に置き換え、ファイルを保存して閉じます。  
  
    > [!NOTE]  
    >  次の XML は、Visual C# の項目テンプレート用です。 Visual Basic の項目テンプレートを作成する場合は、`ProjectType` 要素の値を `VisualBasic` に置き換えてください。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     このファイルには、項目テンプレートの内容と動作が定義されています。 このファイルの内容に関する詳細については、次を参照してください。 [Visual Studio テンプレート スキーマ参照](/visualstudio/extensibility/visual-studio-template-schema-reference)します。  
  
4.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ItemTemplate**プロジェクトで、選択**追加**を選び、**新しい項目の**。  
  
5.  **新しい項目の追加** ダイアログ ボックスで、選択、**テキスト ファイル**テンプレート。  
  
6.  **名前**ボックスに、入力**CustomAction.spdata**、選択し、**追加**ボタンをクリックします。  
  
7.  次の XML を追加、 *CustomAction.spdata*ファイルを保存し、ファイルを閉じます。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     このファイルには、プロジェクト項目に含まれている各ファイルに関する情報が格納されます。 `Type` 要素の `ProjectItem` 属性には、プロジェクト項目定義 (先ほど作成した <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> クラス) の `CustomActionProjectItemTypeProvider` に渡した文字列を設定します。 内容の詳細については *.spdata*ファイルを参照してください[SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)します。  
  
8.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ItemTemplate**プロジェクトで、選択**追加**を選び、**新しい項目の**。  
  
9. **新しい項目の追加** ダイアログ ボックスで、選択、 **XML ファイル**テンプレート。  
  
10. **名前**ボックスに、入力**Elements.xml**、選択し、**追加**ボタンをクリックします。  
  
11. 内容を置き換える、 *Elements.xml*を次の XML ファイルを保存し、ファイルを閉じます。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     このファイルにメニュー項目を作成する既定のカスタム アクションを定義する、**サイトの操作**SharePoint サイトのメニュー。 ユーザーがメニュー項目をクリックすると、`UrlAction` 要素に指定された URL が Web ブラウザーに表示されます。 カスタム アクションを定義に使用できる XML 要素の詳細については、次を参照してください。[カスタム アクション定義](http://go.microsoft.com/fwlink/?LinkId=177801)します。  
  
12. 必要に応じて、開く、 *ItemTemplate.ico*ファイルし、認識できるデザインするように変更します。 プロジェクト項目の横にあるこのアイコンが表示されます、**新しい項目の追加** ダイアログ ボックス。  
  
13. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ItemTemplate**プロジェクトを選び、**プロジェクトのアンロード**します。  
  
14. ショートカット メニューを開き、 **ItemTemplate**プロジェクトをもう一度、 **itemtemplate.csproj の編集**または**itemtemplate.vbproj の編集**します。  
  
15. プロジェクト ファイルで次の `VSTemplate` 要素を見つけます。  
  
    ```xml  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. `VSTemplate` 要素を次の XML に置き換え、ファイルを保存して閉じます。  
  
    ```xml  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 要素は、プロジェクトをビルドすると項目テンプレートが作成されるパス内の追加フォルダーを指定します。 ここで指定したフォルダーは、顧客を開く場合にのみ、項目テンプレートが利用できるということを確認、**新しい項目の追加** ダイアログ ボックスで、展開、 **SharePoint**ノードを選択し、 **2010**ノード。  
  
17. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ItemTemplate**プロジェクトを選び、**プロジェクトの再読み込み**します。  
  
## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>プロジェクト アイテムを配置するための VSIX パッケージを作成します。
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。 まず、VSIX プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更して、VSIX パッケージを構成します。 次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX パッケージを構成および作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **source.extension.vsixmanifest**ファイル、CustomActionProjectItem プロジェクトを選び、**開く**します。  
  
     Visual Studio によってマニフェスト エディターでファイルが開きます。 source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)します。  
  
2.  **製品名**ボックスに、入力**Custom Action Project Item**します。  
  
3.  **作成者**ボックスに、入力**Contoso**します。  
  
4.  **説明**ボックスに、入力**カスタム アクションを表す SharePoint プロジェクト項目**します。  
  
5.  **資産** タブで、選択、**新規**ボタンをクリックします。  
  
     **新しい資産の追加** ダイアログ ボックスが表示されます。  
  
6.  **型**一覧で、選択 **[microsoft.visualstudio.itemtemplate]** します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `ItemTemplate` 要素に対応します。 プロジェクト項目テンプレートが格納される VSIX パッケージ内のサブフォルダーは、この要素によって指定されます。 詳細については、次を参照してください。 [ItemTemplate の要素 (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\))します。  
  
7.  **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。  
  
8.  **プロジェクト**一覧で、選択**ItemTemplate**、選択し、 **OK**ボタン。  
  
9. **資産** タブで、選択、**新規**もう一度ボタンをクリックします。  
  
     **新しい資産の追加** ダイアログ ボックスが表示されます。  
  
10. **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))します。  
  
11. **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。  
  
12. **プロジェクト**一覧で、選択**ProjectItemDefinition**します。  
  
13. **[OK]** を選択します。  
  
14. メニュー バーで、**ビルド** > **ソリューションのビルド**のエラーのないプロジェクトをコンパイルできるかどうかを確認します。  
  
15. CustomActionProjectItem プロジェクトのビルド出力フォルダーに CustomActionProjectItem.vsix ファイルが格納されていることを確認します。  
  
     既定では、ビルド出力フォルダーは ..\bin\Debug で、CustomActionProjectItem プロジェクトが格納されているフォルダーの下にあります。  
  
## <a name="test-the-project-item"></a>プロジェクト項目をテストします。
 これで、プロジェクト項目をテストする準備ができました。 まず、Visual Studio の実験用インスタンスで CustomActionProjectItem ソリューションのデバッグを開始します。 次に、テスト、**カスタム アクション**Visual Studio の実験用インスタンスで、SharePoint プロジェクト内のプロジェクト アイテム。 最後に、SharePoint プロジェクトをビルドして実行し、カスタム動作が正常に機能することを確認します。  
  
#### <a name="to-start-debugging-the-solution"></a>ソリューションのデバッグを開始するには  
  
1.  管理者の資格情報で Visual Studio を再起動し、CustomActionProjectItem ソリューションを開きます。  
  
2.  CustomAction コード ファイルを開き、`InitializeType` メソッドのコードの先頭行にブレークポイントを追加します。  
  
3.  選択、 **F5**キー デバッグを開始します。  
  
     Visual Studio によって、拡張機能が %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Action Project Item\1.0 にインストールされ、Visual Studio の実験用インスタンスが開始されます。 このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### <a name="to-test-the-project-item-in-visual-studio"></a>Visual Studio でプロジェクト項目をテストするには  
  
1.  メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ファイル** > **新規** > **プロジェクト**します。  
  
2.  展開**Visual c#** または**Visual Basic** (言語に応じて、項目テンプレートがサポートする)、展開**SharePoint**を選択し、 **2010**ノード。  
  
3.  プロジェクト テンプレートの一覧で選択**SharePoint 2010 プロジェクト**します。  
  
4.  **名前**ボックスに、入力**CustomActionTest**、選択し、 **OK**ボタン。  
  
5.  **SharePoint カスタマイズ ウィザード**、デバッグに使用するサイトの URL を入力し、、**完了**ボタンをクリックします。  
  
6.  **ソリューション エクスプ ローラー**、プロジェクト ノードのショートカット メニューを開き、**追加**を選び、**新しい項目の**します。  
  
7.  **新しい項目の追加** ダイアログ ボックスで、選択、 **2010**ノードの下、 **SharePoint**ノード。  
  
     いることを確認、**カスタム アクション**プロジェクト項目の一覧で項目が表示されます。  
  
8.  選択、**カスタム アクション**項目をクリックして、**追加**ボタンをクリックします。  
  
     Visual Studio がという名前の項目を追加します**CustomAction1**開きますをプロジェクトに、 *Elements.xml*ファイルがエディターでします。  
  
9. Visual Studio のもう一方のインスタンスで、先ほど `InitializeType` メソッドに設定したブレークポイントで、コードが停止していることを確認します。  
  
10. 選択、 **F5**プロジェクトのデバッグを続行するキー。  
  
11. Visual Studio の実験用インスタンスで**ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **CustomAction1**ノードを選び、 **カスタム動作デザイナー**.  
  
12. メッセージ ボックスが表示されたら、ことを確認し、 **OK**ボタンをクリックします。  
  
     このショートカット メニューを使用して、追加のオプションやコマンド (カスタム動作のデザイナーを表示するなど) を開発者に提供することができます。  
  
13. メニュー バーで、**ビュー** > **出力**します。  
  
     **出力**ウィンドウが開きます。  
  
14. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **CustomAction1**項目、およびその名前を変更**MyCustomAction**します。  
  
     **出力**ウィンドウで、確認メッセージが表示されます。 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> クラスに定義した `CustomActionProjectItemTypeProvider` イベント ハンドラーによってメッセージが出力されます。 このイベントを初めとする、プロジェクト項目の各種イベントを処理することにより、プロジェクト項目に対して開発者が変更を加えたときのカスタム動作を実装することができます。  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint のカスタム動作をテストするには  
  
1.  Visual Studio の実験用インスタンスを開き、 *Elements.xml*の子であるファイル、 **MyCustomAction**プロジェクト アイテム。  
  
2.  *Elements.xml*ファイル、次の変更を加えるし、ファイルを保存します。  
  
    -   `CustomAction` 要素で、次の例に示すように、`Id` 属性を GUID などの一意の文字列に設定します。  
  
        ```xml  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   `CustomAction` 要素で、次の例に示すように、`Title` 属性を設定します。  
  
        ```xml  
        Title="SharePoint Developer Center"  
        ```  
  
    -   `CustomAction` 要素で、次の例に示すように、`Description` 属性を設定します。  
  
        ```xml  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   `UrlAction` 要素で、次の例に示すように、`Url` 属性を設定します。  
  
        ```xml  
        Url="https://docs.microsoft.com/sharepoint/dev/"  
        ```  
  
3.  **F5** キーを押します。  
  
     カスタム アクションをパッケージ化されで指定されている SharePoint サイトに配置された、**サイトの URL**プロジェクトのプロパティ。 Web ブラウザーには、このサイトの既定のページが表示されます。  
  
    > [!NOTE]  
    >  場合、**スクリプト デバッグが無効**選択 ダイアログ ボックスが表示されたら、**はい**クリックしてプロジェクトのデバッグを続行します。  
  
4.  **サイトの操作**] メニューの [選択**SharePoint デベロッパー センター**、ブラウザーが web サイトを開くことを確認します。 [https://docs.microsoft.com/sharepoint/dev/](https://docs.microsoft.com/sharepoint/dev/) 、し、web ブラウザーを閉じます。  
  
## <a name="clean-up-the-development-computer"></a>開発用コンピューターをクリーンアップします。
 プロジェクト項目のテストが終わったら、プロジェクト項目テンプレートを Visual Studio の実験用インスタンスから削除します。  
  
#### <a name="to-clean-up-the-development-computer"></a>開発コンピューターをクリーンアップするには  
  
1.  メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ツール** > **拡張機能と更新**します。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択**Custom Action Project Item**、選択し、**アンインストール**ボタンをクリックします。  
  
3.  ダイアログ ボックスが表示されますが、選択、**はい**ボタン拡張機能をアンインストールすることを確認します。  
  
4.  選択、**今すぐ再起動**アンインストールを完了するボタンをクリックします。  
  
5.  Visual Studio の実験用インスタンスと、CustomActionProjectItem ソリューションが開いているインスタンスの両方を閉じます。  
  
## <a name="next-steps"></a>次の手順
 このチュートリアルを完了すると、項目テンプレートにウィザードを追加できるようになります。 ウィザードが (その場所や、動作が選択されたときの移動先 URL) などのアクションに関する情報を収集するユーザーは、SharePoint プロジェクトにカスタム動作プロジェクト項目を追加するときにこの情報を追加し、 *Elements.xml*で新しいプロジェクト項目ファイル。 詳細については、次を参照してください。[チュートリアル: 項目テンプレート、第 2 部でのカスタム動作プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)です。  
  
## <a name="see-also"></a>関連項目
 [チュートリアル: 項目テンプレート、第 2 部でのカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [SharePoint プロジェクト サービスを使用します。](../sharepoint/using-the-sharepoint-project-service.md)   
 [Visual Studio テンプレート スキーマ参照](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [アイコン用イメージ エディター](/cpp/windows/image-editor-for-icons)   
 [アイコンまたはその他のイメージの作成&#40;アイコン用イメージ エディター&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
