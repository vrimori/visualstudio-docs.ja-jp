---
title: "Deploying Extensions for the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, deploying extensions"
ms.assetid: 69927d95-acdf-4fd8-ac43-28e9a7fa8a38
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Deploying Extensions for the SharePoint Tools in Visual Studio
  SharePoint ツールの拡張機能を配置するには、拡張機能アセンブリと、拡張機能に同梱する必要のあるその他のファイルを含む [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 拡張機能 \(VSIX\) パッケージを作成します。  VSIX パッケージは、Open Packaging Conventions \(OPC\) 標準に準拠した圧縮ファイルです。  VSIX パッケージには .vsix の拡張子が付いています。  
  
 VSIX パッケージを作成すると、作成した拡張機能を、他のユーザーが .vsix ファイルを実行してインストールできます。  作成した拡張機能を他のユーザーがインストールすると、すべてのファイルは %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions フォルダーに格納されます。  拡張機能を配置するには、[Visual Studio Gallery \(Visual Studio ギャラリー\)](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトに VSIX パッケージをアップロードするか、ネットワーク共有やその他の Web サイトでパッケージをホスティングするなど、他の方法で顧客にパッケージを配布できます。  
  
 VSIX パッケージの作成と、[Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847)への配置の詳細については、「[Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)」を参照してください。  
  
 VSIX パッケージは、Visual Studio の **VSIX プロジェクト** テンプレートを使用するか、手動で作成します。  
  
## VSIX プロジェクトを使用した VSIX パッケージの作成  
 Visual Studio SDK によって提供される **VSIX プロジェクト** テンプレートを使用し、SharePoint ツールの拡張機能の VSIX パッケージを作成できます。  VSIX プロジェクトによる VSIX パッケージの作成は、手動で作成する場合に比べて次のような利点があります。  
  
-   プロジェクトが構築されると、Visual Studio は VSIX パッケージを自動的に生成します。  パッケージへの配置ファイルの追加や、パッケージの \[Content\_Types\].xml ファイルの作成などのタスクは、自動的に実行されます。  
  
-   拡張機能プロジェクトやその他のファイル \(プロジェクト テンプレート、項目テンプレートなど\) のビルド出力を VSIX パッケージに含めるよう、VSIX プロジェクトを設定できます。  
  
 VSIX プロジェクトの使用方法の詳細については、「[VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)」を参照してください。  
  
### プロジェクトの整理  
 既定では、VSIX プロジェクトはアセンブリを生成せず、VSIX パッケージのみを生成します。  そのため、通常は、VSIX プロジェクトには SharePoint ツールの拡張機能を実装しません。  一般的には、少なくとも次の 2 つのプロジェクトを操作します。  
  
-   VSIX プロジェクト。  
  
-   拡張機能を実装するクラス ライブラリ プロジェクト。  
  
 特定の種類の拡張機能の場合、次のような追加のプロジェクトを操作することもあります。  
  
-   拡張機能で使用される SharePoint コマンドを実装するクラス ライブラリ プロジェクト。  このシナリオを示すチュートリアルについては、「[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)」を参照してください。  
  
-   項目テンプレートまたはプロジェクト テンプレートを作成する項目テンプレート プロジェクトまたはプロジェクト テンプレート プロジェクト \(拡張機能で SharePoint プロジェクト項目の新しい種類を定義する場合\)。  このシナリオを示すチュートリアルについては、「[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)」を参照してください。  
  
-   項目テンプレートまたはプロジェクト テンプレートのカスタム ウィザードを実装するクラス ライブラリ プロジェクト \(拡張機能にテンプレートが含まれる場合\)。  このシナリオを示すチュートリアルについては、「[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)」を参照してください。  
  
 すべてのプロジェクトを同じ Visual Studio ソリューションに含める場合は、VSIX プロジェクトの source.extension.vsixmanifest ファイルを修正し、クラス ライブラリ プロジェクトのビルド出力を含めることができます。  
  
### VSIX マニフェストの編集  
 拡張機能に含めるすべての項目のエントリを含むように、VSIX プロジェクトの source.extension.vsixmanifest ファイルを編集する必要があります。  ショートカット メニューのsource.extension.vsixmanifestファイルを開くと、ファイルがファイルのXMLを編集するためのUIを提供するデザイナーに表示されます。  詳細については、「[VSIX マニフェスト デザイナー](../extensibility/media/vsix-manifest-designer.png)」を参照してください。  
  
 次の項目のエントリを source.extension.vsixmanifest ファイルに追加する必要があります。  
  
-   拡張機能アセンブリ。  
  
-   拡張機能で使用される SharePoint コマンドを実装するアセンブリ。  
  
-   拡張機能に関連付けられているプロジェクト テンプレートまたは項目テンプレート。  
  
-   拡張機能に関連付けられているテンプレートのカスタム ウィザード。  
  
 次の手順は、これらの各項目のエントリを .vsixmanifest ファイルに追加する方法を示しています。  
  
##### 拡張機能アセンブリを含めるには  
  
1.  VSIXプロジェクトで、source.extension.vsixmanifestファイルのショートカット メニューを開き、**\[開く\]**を選択します。  
  
     デザイナーでファイルが開きます  
  
2.  エディターの **\[資産\]** のタブで、**\[新規作成\]** のボタンをクリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
3.  **\[種類\]** の一覧で、**\[Microsoft.VisualStudio.MefComponent\]**を選択します。  
  
4.  **\[ソース\]** の一覧で、次の手順のいずれかを実行します: 1  
  
    -   拡張機能アセンブリが、VSIXプロジェクトと同じソリューションにあるプロジェクトから構築 **\[現在のソリューション内のプロジェクト\]**、を選択します。  **\[プロジェクト\]** の一覧で、プロジェクトの名前を選択します。  
  
    -   プロジェクトのファイルが、**\[ファイル システム上のファイル\]**を選択すると、拡張機能アセンブリが含まれているとします。  **\[パス\]** の一覧で、完全パスに拡張機能のアセンブリ ファイルを入力するか、またはアセンブリ ファイルを見つけて選択するために **\[参照\]** のボタンを使用します。  
  
5.  **\[OK\]** を選択します。  
  
##### SharePoint コマンド アセンブリを含めるには  
  
1.  VSIXプロジェクトで、source.extension.vsixmanifestファイルのショートカット メニューを開き、**\[開く\]** のボタンをクリックします。  
  
     ファイルがデザイナーで開かれます。  
  
2.  エディターの **\[資産\]** のセクションでは、**\[新規作成\]** のボタンをクリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
3.  **\[種類\]** ボックスに、**\[SharePoint.Commands.v4\]**を入力します。  
  
4.  **\[ソース\]** の一覧で、次の手順のいずれかを実行します: 1  
  
    -   コマンド アセンブリが、VSIXプロジェクトと同じソリューションにあるプロジェクトから構築 **\[現在のソリューション内のプロジェクト\]**、を選択します。  **\[プロジェクト\]** の一覧で、プロジェクトの名前を選択します。  
  
    -   プロジェクトのファイルが、**\[ファイル システム上のファイル\]**を選択すると、コマンド アセンブリが含まれています。  **\[パス\]** の一覧で、完全パスに拡張機能のアセンブリ ファイルを入力するか、またはアセンブリ ファイルを見つけて選択するために **\[参照\]** のボタンを使用します。  
  
5.  **\[OK\]** を選択します。  
  
##### 作成するテンプレートを含めるには  
  
1.  VSIXプロジェクトで、source.extension.vsixmanifestファイルのショートカット メニューを開き、**\[開く\]** のボタンをクリックします。  
  
     ファイルがデザイナーで開かれます。  
  
2.  エディターの **\[資産\]** のセクションでは、**\[新規作成\]** のボタンをクリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
3.  **\[種類\]** の一覧で、**\[Microsoft.VisualStudio.ProjectTemplate\]** か **\[Microsoft.VisualStudio.ItemTemplate\]**を選択します。  
  
4.  **\[ソース\]** の一覧で、**\[現在のソリューション内のプロジェクト\]**を選択します。  
  
5.  **\[プロジェクト\]** の一覧で、プロジェクトの名前を選択し、**\[OK\]** のボタンをクリックします。  
  
6.  **\[ソリューション エクスプローラー\]**で、プロジェクト テンプレート プロジェクトまたは項目テンプレート プロジェクトのショートカット メニューを開き、**\[プロジェクトのアンロード\]**を選択します。  
  
7.  プロジェクトのノードのショートカット メニューを再度開き、**\[編集\]***YourTemplateProjectName***\[.csproj\]** か **\[編集\]***YourTemplateProjectName***\[.vbproj\]**を選択します。  
  
8.  プロジェクト ファイルで次の `VSTemplate` 要素を見つけます。  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. この要素を次のXMLに置き換えます。  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 要素は、プロジェクトをビルドするとプロジェクト テンプレートが作成されるパス内の追加フォルダーを指定します。  ここで指定するフォルダーは、顧客が **\[新しいプロジェクトの追加\]** のダイアログ ボックスを開いたときにだけ項目テンプレートが使用可能な場合は、**\[SharePoint\]** のノードを展開し、をクリックします **\[2010\]** のノードをであることを確認します。  
  
10. ファイルを保存して閉じます。  
  
11. **\[ソリューション エクスプローラー\]**で、プロジェクト テンプレート プロジェクトまたは項目テンプレート プロジェクトのショートカット メニューを開き、**\[プロジェクトの再読み込み\]**を選択します。  
  
##### 手動で作成するテンプレートを含めるには  
  
1.  VSIX プロジェクトで、テンプレートを格納するプロジェクトに新しいフォルダーを追加します。  
  
2.  この新規フォルダーの下に、次のサブフォルダーを追加し、*LocaleID* フォルダーにテンプレート \(zip\) ファイルを追加します。  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *ロケール ID*  
  
     *YourTemplateName*.zip  
  
     たとえば、英語 \(US\) ロケールに対応した ContosoCustomAction.zip という名前の項目テンプレートがある場合は、完全パスは ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip のようになります。  
  
3.  **\[ソリューション エクスプローラー\]**では、テンプレート ファイル \(*YourTemplateName*の.zip\) を選択します。  
  
4.  **\[プロパティ\]** ウィンドウで、**\[ビルド アクション\]** プロパティを **\[コンテンツ\]** に設定します。  
  
5.  source.extension.vsixmanifestファイルのショートカット メニューを開き、**\[開く\]**を選択します。  
  
     ファイルがデザイナーで開かれます。  
  
6.  エディターの **\[資産\]** のセクションでは、**\[新規作成\]** のボタンをクリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
7.  **\[種類\]** の一覧で、**\[Microsoft.VisualStudio.ItemTemplate\]** か **\[Microsoft.VisualStudio.ProjectTemplate\]**を選択します。  
  
8.  **\[ソース\]** の一覧で、**\[ファイル システム上のファイル\]**を選択します。  
  
9. **\[パス\]** のフィールドで、アセンブリへの完全パスを入力します \(たとえば、アセンブリを見つけて選択するために **\[ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip\]**は、または **\[参照\]** のボタンを使用して **\[OK\]** のボタンを選択します。  
  
##### プロジェクト テンプレートまたは項目テンプレートのウィザードを含めるには  
  
1.  VSIXプロジェクトで、source.extension.vsixmanifestファイルのショートカット メニューを開き、**\[開く\]**を選択します。  
  
     ファイルがデザイナーで開かれます。  
  
2.  エディターの **\[資産\]** のセクションでは、**\[新規作成\]** のボタンをクリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
3.  **\[種類\]** の一覧で、**\[Microsoft.VisualStudio.Assembly\]**を選択します。  
  
4.  **\[ソース\]** の一覧で、次の手順のいずれかを実行します: 1  
  
    -   ウィザード アセンブリが、VSIXプロジェクトと同じソリューションにあるプロジェクトから構築 **\[現在のソリューション内のプロジェクト\]**、を選択します。  **\[プロジェクト\]** の一覧で、プロジェクトの名前を選択します。  
  
    -   プロジェクトのファイルが、**\[ファイル システム上のファイル\]**を選択すると、ウィザード アセンブリが含まれています。  **\[パス\]** のフィールドで、完全パスにアセンブリ ファイルを入力するか、またはアセンブリを見つけて選択するために **\[参照\]** のボタンを使用します。  
  
5.  **\[OK\]** を選択します。  
  
### 関連するチュートリアル  
 次の表に、VSIX プロジェクトを使用してさまざまな種類の SharePoint ツールの拡張機能を配置する方法について説明しているチュートリアルを示します。  
  
|拡張機能の種類|関連するチュートリアル|  
|-------------|-----------------|  
|拡張機能アセンブリのみが含まれる拡張機能|[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|SharePoint コマンドが含まれる拡張機能|[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 2&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Visual Studio テンプレートが含まれる拡張機能|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 1&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|テンプレート ウィザードが含まれる拡張機能|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [チュートリアル: プロジェクト テンプレートに基づくサイト列プロジェクト項目の作成 &#40;パート 2&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## VSIX パッケージの手動作成  
 SharePoint ツールの拡張機能の VSIX パッケージを手動で作成するには、次の手順を実行します。  
  
1.  extension.vsixmanifest ファイル、\[Content\_Types\].xml、および VSIX パッケージ ファイル \(.vsix ファイル\) を作成します。  詳細については、「[VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)」および「[方法: 拡張機能を手動でパッケージ化する &#40;VSIX 配置&#41;](../Topic/How%20to:%20Manually%20Package%20an%20Extension%20(VSIX%20Deployment).md)」を参照してください。  
  
2.  VSIX パッケージに拡張機能アセンブリを追加します。  拡張機能に SharePoint コマンドが含まれる場合は、VSIX パッケージに SharePoint コマンドを実装するアセンブリも追加します。  
  
3.  次のように、extension.vsixmanifest ファイルを修正します。  
  
    -   `Microsoft.VisualStudio.MefComponent` の要素を `Assets` 要素の下に追加し、VSIXパッケージ内の拡張機能を実装するアセンブリの相対パスに新しい要素の値を設定します。  詳細については、「[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/8a813141-8b73-44c9-b80b-ca85bbac9551)」を参照してください。  
  
    -   拡張機能にSharePointのサーバー オブジェクト モデルを呼び出すSharePointコマンドが含まれる場合は、`Assets` 要素の下に `Microsoft.VisualStudio.Assembly` の要素を追加します。  VSIXパッケージ内のSharePointコマンドを実装するアセンブリの相対パスに新しい要素の値を設定します。  詳細については、「[資産の要素 \(VSX スキーマ\)](http://msdn.microsoft.com/ja-jp/9fcfc098-edc7-484b-9d4c-acd17829d737)」を参照してください。  
  
    -   拡張機能にプロジェクト テンプレートまたは項目テンプレートが含まれる場合は、`Assets` 要素の下に `ProjectTemplate` または `ItemTemplate` の要素を追加します。  VSIXパッケージ内のテンプレートを含むフォルダーの相対パスに新しい要素の値を設定します。  詳細については、「[NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/87add64c-9dcd-495f-8815-209dab182cb1)」および「[NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/1d489e54-c1c5-4f96-a510-6c2640867ff0)」を参照してください。  
  
    -   拡張機能にプロジェクト テンプレートまたは項目テンプレートのカスタム ウィザードが含まれる場合は、`Assets` 要素の下に `Assembly` の要素を追加します。  新しい要素の値を、VSIXパッケージ内のアセンブリの相対パスに設定し、完全なアセンブリ名に `AssemblyName` の属性を設定します \(を含むバージョン、カルチャ、および公開キー トークン\)。  詳細については、「[依存関係の要素 \(VSX スキーマ\)](http://msdn.microsoft.com/ja-jp/1f63f60a-98ad-48ec-8e44-4eba383d3e37)」を参照してください。  
  
### 例  
 次の例は、SharePoint ツールの拡張機能の extension.vsixmanifest ファイルの内容を示しています。  拡張機能は、Contoso.ProjectExtension.dllという名前のアセンブリで実装されます。  拡張子は、VSIXパッケージ内の **\[ItemTemplates\]** という名前のフォルダーのContoso.ExtensionCommands.dllと項目テンプレートという名前のSharePointコマンド アセンブリが含まれます。  この例では、どちらのアセンブリも、VSIX パッケージの extension.vsixmanifest ファイルと同じフォルダーにあることを想定しています。  
  
```  
<PackageManifest Version=”2.0.0” xmlns=”http://schemas.microsoft.com/developer/vsx-schema/2011”>  
  <Metadata>  
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />  
    <DisplayName>CustomActionProjectItem</DisplayName>  
    <Description>Empty VSIX Project.</Description>  
  </Metadata>  
  <Installation>  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />  
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />  
  </Assets>  
</PackageManifest>  
  
```  
  
## 参照  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  