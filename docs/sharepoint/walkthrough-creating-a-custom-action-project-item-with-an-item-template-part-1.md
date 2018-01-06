---
title: "チュートリアル: 項目テンプレートにカスタム動作プロジェクト項目の作成、パート 1 |Microsoft ドキュメント"
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
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: 41ed9c1c-4239-4d80-934b-975fde744288
caps.latest.revision: "152"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 70a307fe1eb68cb6e1409d0a43178795f0d9421c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1"></a>チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成します。
  Visual Studio の SharePoint プロジェクト システムは、プロジェクト項目の種類を独自に作成することによって拡張することができます。 このチュートリアルでは、SharePoint サイトでカスタム アクションを作成する SharePoint プロジェクトに追加できるプロジェクト項目を作成します。 カスタム アクションを追加するメニュー項目、**サイトの操作**SharePoint サイトのメニュー。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   カスタム動作のための SharePoint プロジェクト項目の新しい種類を定義する Visual Studio 拡張機能の作成。 この新しいプロジェクト項目の種類では、次に示すいくつかのカスタム機能を実装します。  
  
    -   プロジェクト項目に関連したさまざまな追加タスク (Visual Studio でカスタム動作を作成するためのデザイナーを表示するなど) の開始点となるショートカット メニュー。  
  
    -   開発者がプロジェクト項目やそれを含んでいるプロジェクトの特定のプロパティを変更したときに実行されるコード。  
  
    -   プロジェクト項目の横に表示されるカスタム アイコン**ソリューション エクスプ ローラー**です。  
  
-   対応するプロジェクト項目用の Visual Studio 項目テンプレートを作成する。  
  
-   プロジェクト項目テンプレートや拡張機能のアセンブリを配置するための Visual Studio Extension (VSIX) パッケージを構築する。  
  
-   プロジェクト項目のデバッグとテストを行う。  
  
 これは、独立したチュートリアルです。 このチュートリアルを完了すると、項目テンプレートにウィザードを追加してプロジェクト項目を拡張できるようになります。 詳細については、次を参照してください。[チュートリアル: 項目テンプレート、第 2 部にカスタム動作プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)です。  
  
> [!NOTE]  
>  完成したプロジェクト、コード、およびこのチュートリアルでは、次の場所から他のファイルを含むサンプルをダウンロードすることができます: [http://go.microsoft.com/fwlink/?LinkId=191369](http://go.microsoft.com/fwlink/?LinkId=191369)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows、SharePoint、および Visual Studio。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 このチュートリアルでは、 **VSIX プロジェクト**sdk をプロジェクト項目を配置するための VSIX パッケージを作成するテンプレートです。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツール拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)です。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   SharePoint のカスタム動作。 詳細については、次を参照してください。[カスタム アクション](http://go.microsoft.com/fwlink/?LinkId=177800)です。  
  
-   Visual Studio の項目テンプレート。 詳細については、「[Creating Project and Item Templates](/visualstudio/ide/creating-project-and-item-templates)」 (プロジェクトと項目テンプレートの作成) をご覧ください。  
  
## <a name="creating-the-projects"></a>プロジェクトの作成  
 このチュートリアルを実行するには、3 つのプロジェクトを作成する必要があります。  
  
-   VSIX プロジェクト。 このプロジェクトは、SharePoint プロジェクト項目を配置するための VSIX パッケージを作成します。  
  
-   項目テンプレート プロジェクト。 このプロジェクトは、SharePoint プロジェクト項目を SharePoint プロジェクトに追加するために使用できる項目テンプレートを作成します。  
  
-   クラス ライブラリ プロジェクト。 このプロジェクトは、SharePoint プロジェクト項目の動作を定義する Visual Studio 拡張機能を実装します。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
3.  上部にある一覧で、**新しいプロジェクト** ダイアログ ボックスで、ことを確認して**.NET Framework 4.5**が選択されています。  
  
4.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し、 **Extensibility**ノード。  
  
    > [!NOTE]  
    >  **Extensibility**ノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
5.  選択、 **VSIX プロジェクト**テンプレート。  
  
6.  **名前**ボックスに、入力**CustomActionProjectItem**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]追加、 **CustomActionProjectItem**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
#### <a name="to-create-the-item-template-project"></a>項目テンプレート プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**でソリューション ノードのショートカット メニューを開き、**追加**を選択し**新しいプロジェクト**です。  
  
2.  上部にある一覧で、**新しいプロジェクト** ダイアログ ボックスで、ことを確認して**.NET Framework 4.5**が選択されています。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し、 **Extensibility**ノード。  
  
4.  プロジェクト テンプレートの一覧で選択、 **c# 項目テンプレート**または**Visual Basic 項目テンプレート**テンプレート。  
  
5.  **名前**ボックスに、入力**ItemTemplate**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]追加、 **ItemTemplate**プロジェクトがソリューションにします。  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**でソリューション ノードのショートカット メニューを開き、**追加**を選択し**新しいプロジェクト**です。  
  
2.  上部にある一覧で、**新しいプロジェクト** ダイアログ ボックスで、ことを確認して**.NET Framework 4.5**が選択されています。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択して、 **Windows**  ノード、を選択し**クラス ライブラリ**プロジェクト テンプレート。  
  
4.  **名前**ボックスに、入力**ProjectItemDefinition**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]追加、 **ProjectItemDefinition**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configuring-the-extension-project"></a>拡張機能プロジェクトの構成  
 SharePoint プロジェクト項目の種類を定義するためのコードを記述する前に、コード ファイルおよびアセンブリ参照を拡張機能プロジェクトに追加しておく必要があります。  
  
#### <a name="to-configure-the-project"></a>プロジェクトを構成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProjectItemDefinition**プロジェクトで、選択**追加**、順に選択**新しい項目の**します。  
  
2.  プロジェクト項目の一覧で選択**コード ファイル**です。  
  
3.  **名前**ボックスで、名前を入力します**CustomAction**と適切なファイル名拡張子とを選択し、**追加**ボタンをクリックします。  
  
4.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProjectItemDefinition**プロジェクトをクリックして**参照の追加**です。  
  
5.  **参照マネージャー - ProjectItemDefinition**  ダイアログ ボックスで、選択、**アセンブリ** ノードを選択し、 **Framework**ノード。  
  
6.  次の各アセンブリの横にあるチェック ボックスをオンにします。  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  選択、**拡張機能**ノード、Microsoft.VisualStudio.Sharepoint アセンブリの横にあるチェック ボックスをオンにして、 **OK**ボタンをクリックします。  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>新しい SharePoint プロジェクト項目の種類の定義  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスを実装するクラスを作成して、新しいプロジェクト項目の種類の動作を定義します。 このインターフェイスは、新しい種類のプロジェクト項目を定義するたびに必ず実装します。  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>新しい SharePoint プロジェクト項目の種類を定義するには  
  
1.  ProjectItemDefinition プロジェクトで、CustomAction コード ファイルを開きます。  
  
2.  このファイル内のコードを次のコードに置き換えます。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]  
  
## <a name="creating-an-icon-for-the-project-item-in-solution-explorer"></a>ソリューション エクスプローラーに表示されるプロジェクト項目用アイコンの作成  
 カスタム SharePoint プロジェクト項目を作成した場合、そのプロジェクト項目にはイメージ (アイコンまたはビットマップ) を関連付けることができます。 プロジェクト項目の横にあるこのイメージが表示されます**ソリューション エクスプ ローラー**です。  
  
 次の手順では、プロジェクト項目のアイコンを実際に作成し、拡張機能のアセンブリに埋め込みます。 このアイコンは、先ほど作成した <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> クラスの `CustomActionProjectItemTypeProvider` から参照されます。  
  
#### <a name="to-create-a-custom-icon-for-the-project-item"></a>プロジェクト項目のカスタム アイコンを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProjectItemDefinition**プロジェクト**追加**を選択し**新しい項目の追加しています.**.  
  
2.  プロジェクト項目の一覧で選択、**アイコン ファイル**項目。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで選択する必要があります、**全般**を表示するノード、**アイコン ファイル**項目。  
  
3.  **名前**ボックスに、入力**CustomAction_SolutionExplorer.ico**を選択し、**追加**ボタンをクリックします。  
  
     新しいアイコンが表示されます、**イメージ エディター**です。  
  
4.  認識しやすいデザインとなるよう 16x16 版のアイコン ファイルを編集し、アイコン ファイルを保存します。  
  
5.  **ソリューション エクスプ ローラー**、選択**CustomAction_SolutionExplorer.ico**です。  
  
6.  **プロパティ**ウィンドウで、横の矢印を選択、**ビルド アクション**プロパティです。  
  
7.  表示される一覧で選択**埋め込まれたリソース**です。  
  
## <a name="checkpoint"></a>チェックポイント  
 この段階で、プロジェクト項目に必要なすべてのコードがプロジェクトに揃ったことになります。 エラーが発生することなくプロジェクトをコンパイルできるかどうか、プロジェクトをビルドして確認してください。  
  
#### <a name="to-build-your-project"></a>プロジェクトをビルドするには  
  
1.  ショートカット メニューを開き、 **ProjectItemDefinition**プロジェクト**ビルド**です。  
  
## <a name="creating-a-visual-studio-item-template"></a>Visual Studio 項目テンプレートの作成  
 自分が定義したプロジェクト項目を他の開発者が使用できるようにするには、プロジェクト テンプレートまたは項目テンプレートを作成します。 Visual Studio で新しいプロジェクトを作成する際または既存のプロジェクトに項目を追加する際、開発者は、そのテンプレートを使用して、プロジェクト項目のインスタンスを作成します。 このチュートリアルでは、ItemTemplate プロジェクトを使用してプロジェクト項目を構成します。  
  
#### <a name="to-create-the-item-template"></a>項目テンプレートを作成するには  
  
1.  Class1 コード ファイルを ItemTemplate プロジェクトから削除します。  
  
2.  ItemTemplate プロジェクトで、ItemTemplate.vstemplate ファイルを開きます。  
  
3.  ファイルの内容を次の XML に置き換え、ファイルを保存して閉じます。  
  
    > [!NOTE]  
    >  次の XML は、Visual C# の項目テンプレート用です。 Visual Basic の項目テンプレートを作成する場合は、`ProjectType` 要素の値を `VisualBasic` に置き換えてください。  
  
    ```  
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
  
     このファイルには、項目テンプレートの内容と動作が定義されています。 このファイルの内容に関する詳細については、次を参照してください。 [Visual Studio テンプレート スキーマ参照](/visualstudio/extensibility/visual-studio-template-schema-reference)です。  
  
4.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ItemTemplate**プロジェクト**追加**を選択し**新しい項目の**します。  
  
5.  **新しい項目の追加** ダイアログ ボックスで、選択、**テキストファイル**テンプレート。  
  
6.  **名前**ボックスに、入力**CustomAction.spdata**を選択し、**追加**ボタンをクリックします。  
  
7.  次の XML を CustomAction.spdata ファイルに追加し、ファイルを保存して閉じます。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     このファイルには、プロジェクト項目に含まれている各ファイルに関する情報が格納されます。 `Type` 要素の `ProjectItem` 属性には、プロジェクト項目定義 (先ほど作成した <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> クラス) の `CustomActionProjectItemTypeProvider` に渡した文字列を設定します。 .Spdata ファイルの内容に関する詳細については、次を参照してください。 [SharePoint プロジェクト項目のスキーマ リファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)です。  
  
8.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ItemTemplate**プロジェクト**追加**を選択し**新しい項目の**します。  
  
9. **新しい項目の追加** ダイアログ ボックスで、選択、 **XML ファイル**テンプレート。  
  
10. **名前**ボックスに、入力**Elements.xml**を選択し、**追加**ボタンをクリックします。  
  
11. Elements.xml ファイルの内容を次の XML に置き換え、ファイルを保存して閉じます。  
  
    ```  
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
  
     このファイルにメニュー項目を作成する既定のカスタム アクションを定義する、**サイトの操作**SharePoint サイトのメニュー。 ユーザーがメニュー項目をクリックすると、`UrlAction` 要素に指定された URL が Web ブラウザーに表示されます。 カスタム アクションを定義に使用できる XML 要素の詳細については、次を参照してください。[カスタム アクションの定義](http://go.microsoft.com/fwlink/?LinkId=177801)です。  
  
12. 必要に応じて、ItemTemplate.ico ファイルを開き、わかりやすいデザインに変更します。 プロジェクト項目の横にあるこのアイコンが表示されます、**新しい項目の追加** ダイアログ ボックス。  
  
13. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ItemTemplate**プロジェクトをクリックして**プロジェクトのアンロード**です。  
  
14. ショートカット メニューを開き、 **ItemTemplate**クリックして、もう一度、プロジェクト**itemtemplate.csproj の編集**または**itemtemplate.vbproj の編集**です。  
  
15. プロジェクト ファイルで次の `VSTemplate` 要素を見つけます。  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. `VSTemplate` 要素を次の XML に置き換え、ファイルを保存して閉じます。  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 要素は、プロジェクトをビルドすると項目テンプレートが作成されるパス内の追加フォルダーを指定します。 ここで指定したフォルダーは、顧客が開いたときにだけ、項目テンプレートが使用できることを確認してください、**新しい項目の追加** ダイアログ ボックスで、展開、 **SharePoint**  ノードを選択し、 **2010。**ノード。  
  
17. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ItemTemplate**プロジェクトをクリックして**プロジェクトの再読み込み**です。  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item"></a>プロジェクト項目を配置するための VSIX パッケージの作成  
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。 まず、VSIX プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更して、VSIX パッケージを構成します。 次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX パッケージを構成および作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **source.extension.vsixmanifest** CustomActionProjectItem プロジェクトのファイルし、順に選択**開く**です。  
  
     Visual Studio によってマニフェスト エディターでファイルが開きます。 source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)です。  
  
2.  **Product Name**ボックスに、入力**Custom Action Project Item**です。  
  
3.  **作成者**ボックスに、入力**Contoso**です。  
  
4.  **説明**ボックスに、入力**A SharePoint プロジェクト項目をカスタム アクションを表す**です。  
  
5.  **資産** タブで、選択、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
6.  **型**一覧で、選択**[microsoft.visualstudio.itemtemplate]**です。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `ItemTemplate` 要素に対応します。 プロジェクト項目テンプレートが格納される VSIX パッケージ内のサブフォルダーは、この要素によって指定されます。 詳細については、次を参照してください。 [ItemTemplate 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0)です。  
  
7.  **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
8.  **プロジェクト**一覧で、選択**ItemTemplate**を選択し、 **OK**ボタンをクリックします。  
  
9. **資産** タブで、選択、**新規**を再度クリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
10. **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**です。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)です。  
  
11. **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
12. **プロジェクト**一覧で、選択**ProjectItemDefinition**です。  
  
13. **[OK]** を選択します。  
  
14. メニュー バーで、次のように選択します。**ビルド**、**ソリューションのビルド**、し、プロジェクトをコンパイル エラーが発生しないことを確認します。  
  
15. CustomActionProjectItem プロジェクトのビルド出力フォルダーに CustomActionProjectItem.vsix ファイルが格納されていることを確認します。  
  
     既定では、ビルド出力フォルダーは ..\bin\Debug で、CustomActionProjectItem プロジェクトが格納されているフォルダーの下にあります。  
  
## <a name="testing-the-project-item"></a>プロジェクト項目のテスト  
 これで、プロジェクト項目をテストする準備ができました。 まず、Visual Studio の実験用インスタンスで CustomActionProjectItem ソリューションのデバッグを開始します。 その後、テスト、**カスタム アクション**Visual Studio の実験用インスタンスでの SharePoint プロジェクトでプロジェクト項目です。 最後に、SharePoint プロジェクトをビルドして実行し、カスタム動作が正常に機能することを確認します。  
  
#### <a name="to-start-debugging-the-solution"></a>ソリューションのデバッグを開始するには  
  
1.  管理者の資格情報で Visual Studio を再起動し、CustomActionProjectItem ソリューションを開きます。  
  
2.  CustomAction コード ファイルを開き、`InitializeType` メソッドのコードの先頭行にブレークポイントを追加します。  
  
3.  選択、 **f5 キーを押して**デバッグを開始するキー。  
  
     Visual Studio によって、拡張機能が %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Action Project Item\1.0 にインストールされ、Visual Studio の実験用インスタンスが開始されます。 このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### <a name="to-test-the-project-item-in-visual-studio"></a>Visual Studio でプロジェクト項目をテストするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**です。  
  
2.  展開**Visual c#**または**Visual Basic** (言語によっては、項目テンプレートをサポートする) 展開**SharePoint**を選択し、 **2010**ノード。  
  
3.  プロジェクト テンプレートの一覧で選択**SharePoint 2010 プロジェクト**です。  
  
4.  **名前**ボックスに、入力**CustomActionTest**を選択し、 **OK**ボタンをクリックします。  
  
5.  **SharePoint カスタマイズ ウィザード**、デバッグに使用するサイトの URL を入力し、、**完了**ボタンをクリックします。  
  
6.  **ソリューション エクスプ ローラー**でプロジェクト ノードのショートカット メニューを開き、**追加**を選択し**新しい項目の**します。  
  
7.  **新しい項目の追加** ダイアログ ボックスで、選択、 **2010**ノードの下、 **SharePoint**ノード。  
  
     いることを確認、**カスタム アクション**プロジェクト項目の一覧で項目が表示されます。  
  
8.  選択、**カスタム アクション**項目をクリックして、**追加**ボタンをクリックします。  
  
     Visual Studio はという項目の追加**CustomAction1**プロジェクトおよびエディターに Elements.xml ファイルが開きます。  
  
9. Visual Studio のもう一方のインスタンスで、先ほど `InitializeType` メソッドに設定したブレークポイントで、コードが停止していることを確認します。  
  
10. 選択、 **f5 キーを押して**プロジェクトのデバッグを続行するキー。  
  
11. Visual Studio の実験用インスタンスで**ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **CustomAction1** ] ノードを選択し**[カスタム動作デザイナー**.  
  
12. いることを確認するメッセージ ボックスが表示されたらを選択し、 **OK**ボタンをクリックします。  
  
     このショートカット メニューを使用して、追加のオプションやコマンド (カスタム動作のデザイナーを表示するなど) を開発者に提供することができます。  
  
13. メニュー バーで、次のように選択します。**ビュー**、**出力**です。  
  
     **出力**ウィンドウが開きます。  
  
14. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **CustomAction1**項目、およびその名前を変更**MyCustomAction**です。  
  
     **出力**ウィンドウで、確認メッセージが表示されます。 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> クラスに定義した `CustomActionProjectItemTypeProvider` イベント ハンドラーによってメッセージが出力されます。 このイベントを初めとする、プロジェクト項目の各種イベントを処理することにより、プロジェクト項目に対して開発者が変更を加えたときのカスタム動作を実装することができます。  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint のカスタム動作をテストするには  
  
1.  Visual Studio の実験用インスタンスの子である Elements.xml ファイルを開き、 **MyCustomAction**プロジェクト項目です。  
  
2.  Elements.xml ファイルで、次の変更を行い、ファイルを保存します。  
  
    -   `CustomAction` 要素で、次の例に示すように、`Id` 属性を GUID などの一意の文字列に設定します。  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   `CustomAction` 要素で、次の例に示すように、`Title` 属性を設定します。  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   `CustomAction` 要素で、次の例に示すように、`Description` 属性を設定します。  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   `UrlAction` 要素で、次の例に示すように、`Url` 属性を設定します。  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  F5 キーを押します。  
  
     カスタム アクションをパッケージ化されで指定されている SharePoint サイトに配置された、**サイト URL**プロジェクトのプロパティです。 Web ブラウザーには、このサイトの既定のページが表示されます。  
  
    > [!NOTE]  
    >  場合、**スクリプト デバッグが無効** ダイアログ ボックスが表示されたら、選択、**はい**プロジェクトのデバッグを続行するにはボタン。  
  
4.  **サイトの操作**] メニューの [選択**SharePoint デベロッパー センター**ブラウザーで web サイト http://msdn.microsoft.com/sharepoint/default.aspx が開かれことを確認し、web ブラウザーを閉じます。  
  
## <a name="cleaning-up-the-development-computer"></a>開発コンピューターのクリーンアップ  
 プロジェクト項目のテストが終わったら、プロジェクト項目テンプレートを Visual Studio の実験用インスタンスから削除します。  
  
#### <a name="to-clean-up-the-development-computer"></a>開発コンピューターをクリーンアップするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ツール**、**拡張機能と更新プログラム**です。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択**Custom Action Project Item**を選択し、**アンインストール**ボタンをクリックします。  
  
3.  ダイアログ ボックスが表示されますが、選択、**はい**extension をアンインストールすることを確認するにはボタン。  
  
4.  選択、**今すぐ再起動**ボタンをクリックしてアンインストールを完了します。  
  
5.  Visual Studio の実験用インスタンスと、CustomActionProjectItem ソリューションが開いているインスタンスの両方を閉じます。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを完了すると、項目テンプレートにウィザードを追加できるようになります。 ユーザーがカスタム動作プロジェクト項目を SharePoint プロジェクトに追加するときに、このウィザードは動作についての情報 (その動作が選択されたときに移動するための場所と URL など) を収集し、Elements.xml ファイルの新しいプロジェクト項目にこの情報を追加します。 詳細については、次を参照してください。[チュートリアル: 項目テンプレート、第 2 部にカスタム動作プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)です。  
  
## <a name="see-also"></a>参照  
 [チュートリアル: 項目テンプレート、第 2 部にカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [SharePoint プロジェクト項目の項目テンプレートとプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [SharePoint プロジェクト サービスの使用](../sharepoint/using-the-sharepoint-project-service.md)   
 [Visual Studio テンプレート スキーマ参照](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [アイコン用イメージ エディター](/cpp/windows/image-editor-for-icons)   
 [アイコン &#41; のアイコンまたはその他のイメージ (&) #40 です。 イメージ エディターを作成します。](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  