---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1 | Microsoft Docs"
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
  - "SharePoint project items, creating custom templates"
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 41ed9c1c-4239-4d80-934b-975fde744288
caps.latest.revision: 152
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 151
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1
  Visual Studio の SharePoint プロジェクト システムは、プロジェクト項目の種類を独自に作成することによって拡張することができます。  このチュートリアルでは、SharePoint プロジェクトに追加できるプロジェクト項目を作成します。これは SharePoint サイトにカスタム動作を作成するためのプロジェクト項目です。  SharePoint サイトの **\[サイトの操作\]** メニューに対し、カスタム動作によってメニュー項目を追加します。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   カスタム動作のための SharePoint プロジェクト項目の新しい種類を定義する Visual Studio 拡張機能の作成。  この新しいプロジェクト項目の種類では、次に示すいくつかのカスタム機能を実装します。  
  
    -   プロジェクト項目に関連したさまざまな追加タスク \(Visual Studio でカスタム動作を作成するためのデザイナーを表示するなど\) の開始点となるショートカット メニュー。  
  
    -   開発者がプロジェクト項目やそれを含んでいるプロジェクトの特定のプロパティを変更したときに実行されるコード。  
  
    -   **ソリューション エクスプローラー**で、プロジェクト項目の横に表示されるカスタム アイコン。  
  
-   対応するプロジェクト項目用の Visual Studio 項目テンプレートを作成する。  
  
-   プロジェクト項目テンプレートや拡張機能のアセンブリを配置するための Visual Studio Extension \(VSIX\) パッケージを構築する。  
  
-   プロジェクト項目のデバッグとテストを行う。  
  
 これは、独立したチュートリアルです。  このチュートリアルを完了すると、項目テンプレートにウィザードを追加してプロジェクト項目を拡張できるようになります。  詳細については、「[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)」を参照してください。  
  
> [!NOTE]  
>  このチュートリアル用の完全なプロジェクト、コード、およびその他のファイルを含むサンプルは、[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369) からダウンロードできます。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows、SharePoint、および Visual Studio。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  このチュートリアルでは、プロジェクト項目を配置するための VSIX パッケージを、SDK の **VSIX プロジェクト** テンプレートを使用して作成します。  詳細については、「[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   SharePoint のカスタム動作。  詳細については、「[カスタム アクション](http://go.microsoft.com/fwlink/?LinkId=177800)」を参照してください。  
  
-   Visual Studio の項目テンプレート。  詳細については、「[Visual Studio でのカスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)」を参照してください。  
  
## プロジェクトの作成  
 このチュートリアルを実行するには、3 つのプロジェクトを作成する必要があります。  
  
-   VSIX プロジェクト。  このプロジェクトは、SharePoint プロジェクト項目を配置するための VSIX パッケージを作成します。  
  
-   項目テンプレート プロジェクト。  このプロジェクトは、SharePoint プロジェクト項目を SharePoint プロジェクトに追加するために使用できる項目テンプレートを作成します。  
  
-   クラス ライブラリ プロジェクト。  このプロジェクトは、SharePoint プロジェクト項目の動作を定義する Visual Studio 拡張機能を実装します。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
3.  **\[新しいプロジェクト\]** ダイアログ ボックスの上部にある一覧で **\[.NET Framework 4.5\]** が選択されていることを確認します。  
  
4.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[Visual C\#\]** ノードまたは **\[Visual Basic\]** ノードを展開し、**\[機能拡張\]** ノードをクリックします。  
  
    > [!NOTE]  
    >  **\[機能拡張\]** ノードは、Visual Studio SDK がインストールされている場合にのみ使用できます。  詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
5.  **\[VSIX プロジェクト\]** テンプレートを選択します。  
  
6.  **\[Name\]** ボックスに「**CustomActionProjectItem**」と入力し、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の**ソリューション エクスプローラー**に **CustomActionProjectItem** プロジェクトが追加されます。  
  
#### 項目テンプレート プロジェクトを作成するには  
  
1.  **ソリューション エクスプローラー**でソリューション ノードのショートカット メニューを開き、**\[追加\]**、**\[新しいプロジェクト\]** の順にクリックします。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで**ソリューション エクスプローラー**にソリューション ノードが表示されるのは、[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)の **\[常にソリューションを表示\]** チェック ボックスがオンになっている場合だけです。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの上部にある一覧で **\[.NET Framework 4.5\]** が選択されていることを確認します。  
  
3.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[Visual C\#\]** ノードまたは **\[Visual Basic\]** ノードを展開し、**\[機能拡張\]** ノードをクリックします。  
  
4.  プロジェクト テンプレートの一覧で **\[C\# 項目テンプレート\]** または **\[Visual Basic 項目テンプレート\]** テンプレートを選択します。  
  
5.  **\[名前\]** ボックスに「**ItemTemplate**」と入力し、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のソリューションに **ItemTemplate** プロジェクトが追加されます。  
  
#### 拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプローラー**でソリューション ノードのショートカット メニューを開き、**\[追加\]**、**\[新しいプロジェクト\]** の順にクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの上部にある一覧で **\[.NET Framework 4.5\]** が選択されていることを確認します。  
  
3.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[Visual C\#\]** ノードまたは **\[Visual Basic\]** ノードを展開します。次に、**\[Windows\]** ノード、**\[クラス ライブラリ\]** プロジェクト テンプレートの順にクリックします。  
  
4.  **\[名前\]** ボックスに「**ProjectItemDefinition**」と入力し、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、**ProjectItemDefinition** プロジェクトがソリューションに追加され、既定の Class1 コード ファイルが開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## 拡張機能プロジェクトの構成  
 SharePoint プロジェクト項目の種類を定義するためのコードを記述する前に、コード ファイルおよびアセンブリ参照を拡張機能プロジェクトに追加しておく必要があります。  
  
#### プロジェクトを構成するには  
  
1.  **ソリューション エクスプローラー**で **\[ProjectItemDefinition\]** プロジェクトのショートカット メニューを開き、**\[追加\]**、**\[新しい項目\]** の順にクリックします。  
  
2.  プロジェクト項目の一覧で **\[コード ファイル\]** を選択します。  
  
3.  **\[名前\]** ボックスに「**CustomAction**」という名前と適切なファイル名拡張子を入力し、**\[追加\]** をクリックします。  
  
4.  **ソリューション エクスプローラー**で、**\[ProjectItemDefinition\]** プロジェクトのショートカット メニューを開き、**\[参照の追加\]** をクリックします。  
  
5.  **\[参照マネージャー \- ProjectItemDefinition\]** ダイアログ ボックスで、**\[アセンブリ\]** ノード、**\[フレームワーク\]** ノードの順にクリックします。  
  
6.  次の各アセンブリの横にあるチェック ボックスをオンにします。  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  **\[拡張機能\]** ノードを選択し、Microsoft.VisualStudio.Sharepoint アセンブリの横にあるチェック ボックスをオンにして、**\[OK\]** をクリックします。  
  
## 新しい SharePoint プロジェクト項目の種類の定義  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> インターフェイスを実装するクラスを作成して、新しいプロジェクト項目の種類の動作を定義します。  このインターフェイスは、新しい種類のプロジェクト項目を定義するたびに必ず実装します。  
  
#### 新しい SharePoint プロジェクト項目の種類を定義するには  
  
1.  ProjectItemDefinition プロジェクトで、CustomAction コード ファイルを開きます。  
  
2.  このファイル内のコードを次のコードに置き換えます。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/projectitemdefinition/customaction.vb#1)]  
  
## ソリューション エクスプローラーに表示されるプロジェクト項目用アイコンの作成  
 カスタム SharePoint プロジェクト項目を作成した場合、そのプロジェクト項目にはイメージ \(アイコンまたはビットマップ\) を関連付けることができます。  **ソリューション エクスプローラー**には、このイメージがプロジェクト項目の横に表示されます。  
  
 次の手順では、プロジェクト項目のアイコンを実際に作成し、拡張機能のアセンブリに埋め込みます。  このアイコンは、先ほど作成した `CustomActionProjectItemTypeProvider` クラスの <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> から参照されます。  
  
#### プロジェクト項目のカスタム アイコンを作成するには  
  
1.  **ソリューション エクスプローラー**で **\[ProjectItemDefinition\]** プロジェクトのショートカット メニューを開き、**\[追加\]**、**\[新しい項目\]** の順にクリックします。  
  
2.  プロジェクト項目の一覧で **\[アイコン ファイル\]** 項目を選択します。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトの場合、**\[アイコン ファイル\]** 項目を表示するには、**\[全般\]** ノードをクリックする必要があります。  
  
3.  **\[名前\]** ボックスに「**CustomAction\_SolutionExplorer.ico**」と入力し、**\[追加\]** をクリックします。  
  
     **イメージ エディター**に新しいアイコンが表示されます。  
  
4.  認識しやすいデザインとなるよう 16x16 版のアイコン ファイルを編集し、アイコン ファイルを保存します。  
  
5.  **ソリューション エクスプローラー**で **\[CustomAction\_SolutionExplorer.ico\]** をクリックします。  
  
6.  **\[プロパティ\]** ウィンドウで、**\[ビルド アクション\]** プロパティの横にある矢印をクリックします。  
  
7.  表示された一覧で **\[埋め込まれたリソース\]** を選択します。  
  
## チェックポイント  
 この段階で、プロジェクト項目に必要なすべてのコードがプロジェクトに揃ったことになります。  エラーが発生することなくプロジェクトをコンパイルできるかどうか、プロジェクトをビルドして確認してください。  
  
#### プロジェクトをビルドするには  
  
1.  **\[ProjectItemDefinition\]** プロジェクトのショートカット メニューを開き、**\[ビルド\]** をクリックします。  
  
## Visual Studio 項目テンプレートの作成  
 自分が定義したプロジェクト項目を他の開発者が使用できるようにするには、プロジェクト テンプレートまたは項目テンプレートを作成します。  Visual Studio で新しいプロジェクトを作成する際または既存のプロジェクトに項目を追加する際、開発者は、そのテンプレートを使用して、プロジェクト項目のインスタンスを作成します。  このチュートリアルでは、ItemTemplate プロジェクトを使用してプロジェクト項目を構成します。  
  
#### 項目テンプレートを作成するには  
  
1.  Class1 コード ファイルを ItemTemplate プロジェクトから削除します。  
  
2.  ItemTemplate プロジェクトで、ItemTemplate.vstemplate ファイルを開きます。  
  
3.  ファイルの内容を次の XML に置き換え、ファイルを保存して閉じます。  
  
    > [!NOTE]  
    >  次の XML は、Visual C\# の項目テンプレート用です。  Visual Basic の項目テンプレートを作成する場合は、`ProjectType` 要素の値を `VisualBasic` に置き換えてください。  
  
    ```  
  
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
  
     このファイルには、項目テンプレートの内容と動作が定義されています。  このファイルの内容の詳細については、「[Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)」を参照してください。  
  
4.  **ソリューション エクスプローラー**で **\[ItemTemplate\]** プロジェクトのショートカット メニューを開き、**\[追加\]**、**\[新しい項目\]** の順にクリックします。  
  
5.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[テキスト ファイル\]** テンプレートを選択します。  
  
6.  **\[名前\]** ボックスに「**CustomAction.spdata**」と入力し、**\[追加\]** をクリックします。  
  
7.  次の XML を CustomAction.spdata ファイルに追加し、ファイルを保存して閉じます。  
  
    ```  
  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     このファイルには、プロジェクト項目に含まれている各ファイルに関する情報が格納されます。  `ProjectItem` 要素の `Type` 属性には、プロジェクト項目定義 \(先ほど作成した `CustomActionProjectItemTypeProvider` クラス\) の <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> に渡した文字列を設定します。  .spdata ファイルの内容の詳細については、「[SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)」を参照してください。  
  
8.  **ソリューション エクスプローラー**で **\[ItemTemplate\]** プロジェクトのショートカット メニューを開き、**\[追加\]**、**\[新しい項目\]** の順にクリックします。  
  
9. **\[新しい項目の追加\]** ダイアログ ボックスで **\[XML ファイル\]** テンプレートを選択します。  
  
10. **\[名前\]** ボックスに「**Elements.xml**」と入力し、**\[追加\]** をクリックします。  
  
11. Elements.xml ファイルの内容を次の XML に置き換え、ファイルを保存して閉じます。  
  
    ```  
  
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
  
     このファイルは、SharePoint サイトの **\[サイトの操作\]** メニューのメニュー項目を作成する既定のカスタム動作を定義します。  ユーザーがメニュー項目をクリックすると、`UrlAction` 要素に指定された URL が Web ブラウザーに表示されます。  カスタム動作の定義に使用できる XML 要素の詳細については、「[カスタム アクション定義スキーマ](http://go.microsoft.com/fwlink/?LinkId=177801)」を参照してください。  
  
12. 必要に応じて、ItemTemplate.ico ファイルを開き、わかりやすいデザインに変更します。  **\[新しい項目の追加\]** ダイアログ ボックスで、対応するプロジェクト項目の横にこのアイコンが表示されます。  
  
13. **ソリューション エクスプローラー**で、**\[ItemTemplate\]** プロジェクトのショートカット メニューを開き、**\[プロジェクトのアンロード\]** をクリックします。  
  
14. **\[ItemTemplate\]** プロジェクトのショートカット メニューを開き、**\[ItemTemplate.csproj の編集\]** または **\[ItemTemplate.vbproj の編集\]** をクリックします。  
  
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
  
     `OutputSubPath` 要素は、プロジェクトをビルドすると項目テンプレートが作成されるパス内の追加フォルダーを指定します。  ここで指定されたフォルダー内の項目テンプレートが使用可能になるのは、顧客が **\[新しい項目の追加\]** ダイアログ ボックスを開き、**\[SharePoint\]** ノードを展開して、**\[2010\]** ノードを選択したときのみです。  
  
17. **ソリューション エクスプローラー**で、**\[ItemTemplate\]** プロジェクトのショートカット メニューを開き、**\[プロジェクトの再読み込み\]** をクリックします。  
  
## プロジェクト項目を配置するための VSIX パッケージの作成  
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。  まず、VSIX プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更して、VSIX パッケージを構成します。  次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### VSIX パッケージを構成および作成するには  
  
1.  **ソリューション エクスプローラー**で、CustomActionProjectItem プロジェクトの **source.extension.vsixmanifest** ファイルのショートカット メニューを開き、**\[開く\]** をクリックします。  
  
     Visual Studio によってマニフェスト エディターでファイルが開きます。  source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。  このファイルの詳細については、「[VSIX 拡張機能のスキーマに関するリファレンス](http://msdn.microsoft.com/ja-jp/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)」を参照してください。  
  
2.  **\[プロジェクト名\]** ボックスに「**Custom Action Project Item**」と入力します。  
  
3.  **\[作成者\]** ボックスに「**Contoso**」と入力します。  
  
4.  **\[説明\]** ボックスに、「**A SharePoint project item that represents a custom action**」\(カスタム動作を表す SharePoint プロジェクト項目\) と入力します。  
  
5.  **\[アセット\]** タブで **\[新規作成\]** をクリックします。  
  
     **\[Add New Asset\]** \(新しいアセットの追加\) ダイアログ ボックスが表示されます。  
  
6.  **\[種類\]** ボックスの一覧で **\[Microsoft.VisualStudio.ItemTemplate\]** を選択します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `ItemTemplate` 要素に対応します。  プロジェクト項目テンプレートが格納される VSIX パッケージ内のサブフォルダーは、この要素によって指定されます。  詳細については、「[NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/1d489e54-c1c5-4f96-a510-6c2640867ff0)」を参照してください。  
  
7.  **\[ソース\]** ボックスの一覧で **\[A project in current solution\]** \(現在のソリューション内のプロジェクト\) を選択します。  
  
8.  **\[プロジェクト\]** ボックスの一覧で **\[ItemTemplate\]** を選択し、**\[OK\]** をクリックします。  
  
9. **\[アセット\]** タブで、もう一度 **\[新規作成\]** をクリックします。  
  
     **\[Add New Asset\]** \(新しいアセットの追加\) ダイアログ ボックスが表示されます。  
  
10. **\[種類\]** ボックスの一覧で **\[Microsoft.VisualStudio.MefComponent\]** を選択します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。  この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。  詳細については、「[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/8a813141-8b73-44c9-b80b-ca85bbac9551)」を参照してください。  
  
11. **\[ソース\]** ボックスの一覧で **\[A project in current solution\]** \(現在のソリューション内のプロジェクト\) を選択します。  
  
12. **\[プロジェクト\]** ボックスの一覧で **\[ProjectItemDefinition\]** を選択します。  
  
13. **\[OK\]** を選択します。  
  
14. メニュー バーで **\[ビルド\]**、**\[ソリューションのビルド\]** の順にクリックし、プロジェクトがエラーなしでコンパイルされたことを確認します。  
  
15. CustomActionProjectItem プロジェクトのビルド出力フォルダーに CustomActionProjectItem.vsix ファイルが格納されていることを確認します。  
  
     既定では、ビルド出力フォルダーは ..\\bin\\Debug で、CustomActionProjectItem プロジェクトが格納されているフォルダーの下にあります。  
  
## プロジェクト項目のテスト  
 これで、プロジェクト項目をテストする準備ができました。  まず、Visual Studio の実験用インスタンスで CustomActionProjectItem ソリューションのデバッグを開始します。  次に、Visual Studio の実験用インスタンスで、SharePoint プロジェクトの**カスタム動作**プロジェクト項目をテストします。  最後に、SharePoint プロジェクトをビルドして実行し、カスタム動作が正常に機能することを確認します。  
  
#### ソリューションのデバッグを開始するには  
  
1.  管理者の資格情報で Visual Studio を再起動し、CustomActionProjectItem ソリューションを開きます。  
  
2.  CustomAction コード ファイルを開き、`InitializeType` メソッドのコードの先頭行にブレークポイントを追加します。  
  
3.  **F5** キーを押してデバッグを開始します。  
  
     Visual Studio によって、拡張機能が %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Custom Action Project Item\\1.0 にインストールされ、Visual Studio の実験用インスタンスが開始されます。  このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### Visual Studio でプロジェクト項目をテストするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで **\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]** の順にクリックします。  
  
2.  \(項目テンプレートがサポートする言語に応じて\) **\[Visual C\#\]** または **\[Visual Basic\]**  を展開し、**\[SharePoint\]** を展開して、**\[2010\]** ノードをクリックします。  
  
3.  プロジェクト テンプレートの一覧で **\[SharePoint 2010 プロジェクト\]** を選択します。  
  
4.  **\[名前\]** ボックスに「**CustomActionTest**」と入力し、**\[OK\]** をクリックします。  
  
5.  **SharePoint カスタマイズ ウィザード**で、デバッグに使用するサイトの URL を入力し、**\[完了\]** をクリックします。  
  
6.  **ソリューション エクスプローラー**でプロジェクトのショートカット メニューを開き、**\[追加\]**、**\[新しい項目\]** の順にクリックします。  
  
7.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[SharePoint\]** ノードの下の **\[2010\]** ノードをクリックします。  
  
     **\[カスタム動作\]** 項目がプロジェクト項目の一覧に表示されることを確認します。  
  
8.  **\[カスタム動作\]** 項目を選択し、**\[追加\]** をクリックします。  
  
     **CustomAction1** という名前の項目がプロジェクトに追加され、エディターに Elements.xml ファイルが表示されます。  
  
9. Visual Studio のもう一方のインスタンスで、先ほど `InitializeType` メソッドに設定したブレークポイントで、コードが停止していることを確認します。  
  
10. **F5** キーを押して、プロジェクトのデバッグを続行します。  
  
11. Visual Studio の実験用インスタンスで、**ソリューション エクスプローラー**を開き、**\[CustomAction1\]** ノードのショートカット メニューを開いて、**\[カスタム動作デザイナーの表示\]** をクリックします。  
  
12. メッセージ ボックスが表示されることを確認して、**\[OK\]** をクリックします。  
  
     このショートカット メニューを使用して、追加のオプションやコマンド \(カスタム動作のデザイナーを表示するなど\) を開発者に提供することができます。  
  
13. メニュー バーで **\[表示\]**、**\[出力\]** の順にクリックします。  
  
     **\[出力\]** ウィンドウが開きます。  
  
14. **ソリューション エクスプローラー**で、**\[CustomAction1\]** 項目のショートカット メニューを開き、その名前を「**MyCustomAction**」に変更します。  
  
     **\[出力\]** ウィンドウに確認メッセージが表示されます。  `CustomActionProjectItemTypeProvider` クラスに定義した <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> イベント ハンドラーによってメッセージが出力されます。  このイベントを初めとする、プロジェクト項目の各種イベントを処理することにより、プロジェクト項目に対して開発者が変更を加えたときのカスタム動作を実装することができます。  
  
#### SharePoint のカスタム動作をテストするには  
  
1.  Visual Studio の実験用インスタンスで、**\[MyCustomAction\]** プロジェクト項目の子である Elements.xml ファイルを開きます。  
  
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
  
     カスタム動作がパッケージ化され、プロジェクトの **\[サイト URL\]** プロパティで指定された SharePoint サイトに配置されます。  Web ブラウザーには、このサイトの既定のページが表示されます。  
  
    > [!NOTE]  
    >  **\[スクリプト デバッグが無効\]** ダイアログ ボックスが表示された場合は、**\[はい\]** をクリックしてプロジェクトをデバッグします。  
  
4.  **\[サイトの操作\]** メニューで **\[SharePoint デベロッパー センター\]** をクリックし、ブラウザーで Web サイト http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx が開かれていること確認したら、Web ブラウザーを閉じます。  
  
## 開発コンピューターのクリーンアップ  
 プロジェクト項目のテストが終わったら、プロジェクト項目テンプレートを Visual Studio の実験用インスタンスから削除します。  
  
#### 開発コンピューターをクリーンアップするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで **\[ツール\]**、**\[拡張機能と更新プログラム\]** の順にクリックします。  
  
     **\[拡張機能と更新プログラム\]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で **\[Custom Action Project Item\]** を選択し、**\[アンインストール\]** をクリックします。  
  
3.  確認のダイアログ ボックスが表示されたら、**\[はい\]** をクリックして、拡張機能をアンインストールします。  
  
4.  **\[今すぐ再起動\]** をクリックするとアンインストールは完了です。  
  
5.  Visual Studio の実験用インスタンスと、CustomActionProjectItem ソリューションが開いているインスタンスの両方を閉じます。  
  
## 次の手順  
 このチュートリアルを完了すると、項目テンプレートにウィザードを追加できるようになります。  ユーザーがカスタム動作プロジェクト項目を SharePoint プロジェクトに追加するときに、このウィザードは動作についての情報 \(その動作が選択されたときに移動するための場所と URL など\) を収集し、Elements.xml ファイルの新しいプロジェクト項目にこの情報を追加します。  詳細については、「[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)」を参照してください。  
  
## 参照  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  