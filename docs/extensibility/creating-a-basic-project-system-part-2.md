---
title: "基本的なプロジェクト システム、第 2 部を作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト システムの書き込み"
  - "プロジェクト システム"
  - "チュートリアル"
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 基本的なプロジェクト システム、第 2 部を作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このシリーズの最初のチュートリアル [基本的なプロジェクト システム、第 1 部を作成します。](../extensibility/creating-a-basic-project-system-part-1.md), 、基本的なプロジェクト システムを作成する方法を示しています。 このチュートリアルでは、Visual Studio テンプレート、プロパティ ページ、およびその他の機能を追加することで、基本的なプロジェクト システムに基づいています。 この 1 つを開始する前に、最初のチュートリアルを完了する必要があります。  
  
 このチュートリアルでは、プロジェクト ファイル名拡張子 .myproj のあるプロジェクトの種類を作成する方法について説明します。 チュートリアルを完了するには、チュートリアルは、既存の Visual c\# プロジェクト システムから借用するために独自の言語を作成する必要はありません。  
  
 このチュートリアルでは、これらのタスクを実行する方法について説明します。  
  
-   Visual Studio のテンプレートを作成します。  
  
-   Visual Studio のテンプレートを展開します。  
  
-   プロジェクトの種類の子ノードを作成、 **新しいプロジェクト** \] ダイアログ ボックス。  
  
-   Visual Studio のテンプレートでパラメーター置換を有効にします。  
  
-   プロジェクトのプロパティ ページを作成します。  
  
> [!NOTE]
>  このチュートリアルの手順では、c\# プロジェクトに基づいています。 ただし、ファイル名拡張子とコードの詳細を除く、Visual Basic プロジェクトと同じ手順を使用できます。  
  
## Visual Studio テンプレートの作成  
 [基本的なプロジェクト システム、第 1 部を作成します。](../extensibility/creating-a-basic-project-system-part-1.md) 基本的なプロジェクト テンプレートを作成し、プロジェクト システムを追加する方法を示します。 使用して Visual Studio でこのテンプレートを登録する方法も示しています、 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 属性には、システム レジストリの \\Templates\\Projects\\SimpleProject\\ フォルダーの完全なパスを書き込みます。  
  
 Visual Studio テンプレート \(.vstemplate ファイル\) を使用すると、基本的なプロジェクト テンプレートではなくで、テンプレートの表示方法を制御できます、 **新しいプロジェクト** \] ダイアログ ボックスとテンプレート パラメーターが次のように置き換えられます。  .Vstemplate ファイルは、ソース ファイルのプロジェクト システム テンプレートを使用して、プロジェクトを作成するときに取り込まれる方法を説明する XML ファイルです。 プロジェクト システム自体が .vstemplate ファイルと、.zip ファイルにソース ファイルを収集して構築され、Visual Studio に認識されている場所に .zip ファイルをコピーして配置します。 このプロセスは、このチュートリアルの後半で詳しく説明します。  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 、に従って作成した SimpleProject ソリューションを開く [基本的なプロジェクト システム、第 1 部を作成します。](../extensibility/creating-a-basic-project-system-part-1.md)します。  
  
2.  SimpleProjectPackage.cs ファイルの検索、ProvideProjectFactory 属性です。 次のように、null、および".\\\\NullPath"と 4 番目のパラメーター \(プロジェクト テンプレート フォルダーへのパス\) を 2 番目のパラメーター \(プロジェクト名\) を置き換えます。  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null, "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj", ".\\NullPath", LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  \\Templates\\Projects\\SimpleProject\\ フォルダーに SimpleProject.vstemplate をという XML ファイルを追加します。  
  
4.  SimpleProject.vstemplate の内容を次のコードに置き換えます。  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"> <TemplateData> <Name>SimpleProject Application</Name> <Description> A project for creating a SimpleProject application </Description> <Icon>SimpleProject.ico</Icon> <ProjectType>SimpleProject</ProjectType> </TemplateData> <TemplateContent> <Project File="SimpleProject.myproj" ReplaceParameters="true"> <ProjectItem ReplaceParameters="true" OpenInEditor="true"> Program.cs </ProjectItem> <ProjectItem ReplaceParameters="true" OpenInEditor="false"> AssemblyInfo.cs </ProjectItem> </Project> </TemplateContent> </VSTemplate>  
    ```  
  
5.  **プロパティ** ウィンドウで、セットの \\Templates\\Projects\\SimpleProject\\ フォルダーでファイルをすべて 5 を選択して、 **ビルド アクション** に **ZipProject**します。  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 \< TemplateData \> セクション SimpleProject プロジェクトの種類の外観と場所を決定する、 **新しいプロジェクト** ダイアログ ボックスで、次のようにします。  
  
-   \< Name \> 要素を SimpleProject アプリケーション プロジェクト テンプレートを名前します。  
  
-   \< Description \> 要素が含まれている説明を表す、 **新しいプロジェクト** \] ダイアログ ボックスのプロジェクト テンプレートを選択するとします。  
  
-   \< Icon \> 要素では、SimpleProject プロジェクトの種類と共に表示されるアイコンを指定します。  
  
-   \< ProjectType \> 要素の名前でプロジェクトの種類、 **新しいプロジェクト** \] ダイアログ ボックス。 この名前は、ProvideProjectFactory 属性のプロジェクトの name パラメーターを置換します。  
  
    > [!NOTE]
    >  \< ProjectType \> 要素に一致する必要があります、 `LanguageVsTemplate` の引数、 `ProvideProjectFactory` SimpleProjectPackage.cs ファイル内の属性です。  
  
 \< TemplateContent \> セクションには、新しいプロジェクトが作成されるときに生成されるこれらのファイルについて説明します。  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   AssemblyInfo.cs  
  
 次の 3 つのすべてのファイルが `ReplaceParameters` により、パラメーター置換を true に設定します。  Program.cs ファイルに `OpenInEditor` 、ファイル、プロジェクトを作成すると、コード エディターで開かれるを true に設定します。  
  
 Visual Studio テンプレート スキーマの要素に関する詳細については、次を参照してください。、 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)です。  
  
> [!NOTE]
>  プロジェクトに複数の Visual Studio テンプレートがある場合は、すべてのテンプレートは、別のフォルダーにです。 そのフォルダー内のすべてのファイルが必要、 **ビルド アクション** 設定 **ZipProject**します。  
  
## 最小限の .vsct ファイルを追加します。  
 Visual Studio は、新しいまたは変更された Visual Studio のテンプレートを認識するセットアップ モードで実行する必要があります。 セットアップ モードには、存在する .vsct ファイルが必要です。 そのため、最小限 .vsct ファイルをプロジェクトに追加する必要があります。  
  
1.  SimpleProject プロジェクトに SimpleProject.vsct をという XML ファイルを追加します。  
  
2.  SimpleProject.vsct ファイルの内容を次のコードに置き換えます。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"> </CommandTable>  
    ```  
  
3.  設定、 **ビルド アクション** するには、このファイルの **VSCTCompile**します。 これを行う、.csproj ファイルでのみではなく、 **プロパティ** ウィンドウです。 確認して、 **ビルド アクション** のこのファイルに設定されている **None** この時点でします。  
  
    1.  SimpleProject ノードを右クリックし、 **編集 SimpleProject.csproj**します。  
  
    2.  .Csproj ファイルでは、SimpleProject.vsct 項目を見つけます。  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  ビルドのアクションを変更する **VSCTCompile**します。  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  プロジェクト ファイルと、エディターを終了します。  
  
    5.  SimpleProject ノードを保存し、次に、 **ソリューション エクスプ ローラー** クリックして **プロジェクトの再読み込み**します。  
  
## Visual Studio テンプレートのビルド手順を確認します。  
 VSPackage プロジェクトのビルド システムは、.vstemplate ファイルが変更されたり、.vstemplate ファイルを含むプロジェクトがリビルドされるときに通常 Visual Studio とセットアップ モードで実行されます。 Normal またはそれ以降、MSBuild の詳細レベルを設定して行うことができます。  
  
1.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
2.  展開、 **プロジェクトおよびソリューション** ノードをクリックして **をビルドおよび実行**します。  
  
3.  設定 **MSBuild プロジェクトのビルド出力の詳細度** に **標準**します。**\[OK\]** をクリックします。  
  
4.  SimpleProject プロジェクトをリビルドします。  
  
 .Zip プロジェクト ファイルを作成するビルド ステップは、次の例のようになります。  
  
```  
ZipProjects: 1>  Zipping ProjectTemplates 1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip... 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip". 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip". 1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip 1>ZipItems: 1>  Zipping ItemTemplates 1>  SimpleProject ->  
```  
  
## Visual Studio テンプレートを展開します。  
 Visual Studio のテンプレートでは、パス情報は含まれません。 そのため、テンプレートの .zip ファイルは、Visual Studio に認識されている場所に配置する必要があります。 ProjectTemplates フォルダーの場所は、通常 **\< %localappdata% \> \\Microsoft\\VisualStudio\\14.0Exp\\ProjectTemplates**します。  
  
 プロジェクト ファクトリを展開するには、管理者特権が、インストール プログラムに必要です。 テンプレート \[Visual Studio のインストール\] ノードを展開します。 **...\\Microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates**します。  
  
## Visual Studio テンプレートのテスト  
 Visual Studio テンプレートを使用してプロジェクト階層を作成しているかどうかを確認、プロジェクトのファクトリをテストします。  
  
1.  Visual Studio SDK 実験用インスタンスをリセットします。  
  
     [!INCLUDE[win7](../debugger/includes/win7_md.md)]: \[スタート\] メニューで、検索、 **Microsoft Visual Studio または Microsoft Visual Studio SDK\/Tools** フォルダー、および選択 **Microsoft Visual Studio 実験用インスタンスをリセット**します。  
  
     以降のバージョンの Windows: \[スタート画面で、「 **Microsoft Visual Studio \< バージョン \> 実験用インスタンスをリセット**します。  
  
2.  コマンド プロンプト ウィンドウが表示されます。 単語が表示されている場合 `Press any key to continue`, 、enter キーを押します。 ウィンドウが閉じて後、は、Visual Studio を開きます。  
  
3.  SimpleProject プロジェクトをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
4.  実験用インスタンスでは、SimpleProject プロジェクトを作成します。**新しいプロジェクト** ダイアログ ボックスで、 **SimpleProject**します。  
  
5.  SimpleProject の新しいインスタンスが表示されます。  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2\_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2\_MyProj")  
  
## プロジェクトの種類の子ノードを作成します。  
 プロジェクトの種類のノードに子ノードを追加することができます、 **新しいプロジェクト** \] ダイアログ ボックス。  たとえば、SimpleProject プロジェクトの種類は、コンソール アプリケーション、ウィンドウのアプリケーション、web アプリケーションの子ノードを持つ可能性があります。  
  
 子ノードは、プロジェクト ファイルを変更し、\< ZipProject \> 要素を \< OutputSubPath \> の子を追加して作成されます。 ビルドまたは配置中に、テンプレートをコピーすると、すべての子ノードには、プロジェクト テンプレート フォルダーのサブフォルダーになります。  
  
 このセクションでは、SimpleProject プロジェクトの種類のコンソールの子ノードを作成する方法を示します。  
  
1.  \\Templates\\Projects\\SimpleProject\\ フォルダーを \\Templates\\Projects\\ConsoleApp\\ に変更します。  
  
2.  **プロパティ** ウィンドウでは、\\Templates\\Projects\\ConsoleApp\\ フォルダーに 5 つのすべてのファイルを選択し、確認、 **ビルド アクション** に設定されている **ZipProject**します。  
  
3.  SimpleProject.vstemplate ファイルでは、終了タグの直前に、\< TemplateData \> セクションの最後に、次の行を追加します。  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     これにより、コンソール アプリケーション テンプレートをコンソールの子ノードと子ノードの 1 つである SimpleProject 親ノードの両方を表示します。  
  
4.  SimpleProject.vstemplate ファイルを保存します。  
  
5.  .Csproj ファイルでは、各 ZipProject 要素に \< OutputSubPath \> を追加します。 以前のようにプロジェクトをアンロードし、プロジェクト ファイルを編集します。  
  
6.  \< ZipProject \> 要素を探します。 各 \< ZipProject \> 要素には、\< OutputSubPath \> 要素を追加し、値コンソールを付けます。 ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico"> <OutputSubPath>Console</OutputSubPath> </ZipProject>  
    ```  
  
7.  この \< PropertyGroup \> をプロジェクト ファイルに追加します。  
  
    ```  
    <PropertyGroup> <VsTemplateLanguage>SimpleProject</VsTemplateLanguage> </PropertyGroup>  
    ```  
  
8.  プロジェクト ファイルを保存し、プロジェクトの再読み込みします。  
  
## プロジェクトの種類の子ノードのテスト  
 変更されたプロジェクト ファイルをテストするかどうか、 **コンソール** で子ノードが表示、 **新しいプロジェクト** \] ダイアログ ボックス。  
  
1.  実行、 **Microsoft Visual Studio の実験用インスタンスをリセット** ツールです。  
  
2.  SimpleProject プロジェクトをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、をクリックして、 **SimpleProject** ノードです。**コンソール アプリケーション** にテンプレートを表示する必要があります、 **テンプレート** ウィンドウです。  
  
4.  展開、 **SimpleProject** ノードです。**コンソール** 子ノードが表示されます。**SimpleProject アプリケーション** テンプレートに引き続き表示されます、 **テンプレート** ウィンドウです。  
  
5.  . クリックして **キャンセル** デバッグを停止  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2\_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2\_Subfolder")  
  
## プロジェクト テンプレートのパラメーターの置換  
 [基本的なプロジェクト システム、第 1 部を作成します。](../extensibility/creating-a-basic-project-system-part-1.md) 上書きする方法を紹介しました、 `ProjectNode.AddFileFromTemplate` 基本的なテンプレート パラメーター置換を実行するメソッドです。 このセクションより高度な Visual Studio のテンプレート パラメーターを使用する方法を説明します。  
  
 Visual Studio テンプレートを使用して、プロジェクトを作成する場合、 **新しいプロジェクト** ダイアログ ボックスで、プロジェクトをカスタマイズする文字列をテンプレート パラメーターに置き換えられます。 テンプレート パラメーターは、先頭し、末尾ドル記号は、たとえば、$time$ を特別なトークンです。 次の 2 つのパラメーターは、テンプレートに基づいてプロジェクトのカスタマイズ機能を有効にするために特に便利です。  
  
-   1 ~ 10 の $GUID$ は、新しい Guid に置き換えられます。 最大 10 の Guid、guid1 $$ などを指定できます。  
  
-   $safeprojectname$ がユーザーによって指定された名前、 **新しいプロジェクト** ダイアログ ボックスで、すべての安全でない文字や空白を削除するように変更します。  
  
 テンプレート パラメーターの一覧については、次を参照してください。 [テンプレート名](../ide/template-parameters.md)します。  独自のカスタム テンプレート パラメーターを作成するを参照して [NIB: 方法: テンプレートへのカスタムのパラメーターを渡す](http://msdn.microsoft.com/ja-jp/5bc2ad11-84c7-4683-a276-e5e00d85d8fb)します。  
  
#### プロジェクト テンプレートのパラメーター値  
  
1.  SimpleProjectNode.cs ファイルで、削除、 `AddFileFromTemplate` メソッドです。  
  
2.  \\Templates\\Projects\\ConsoleApp\\SimpleProject.myproj ファイルで、\< RootNamespace \> のプロパティを見つけて $safeprojectname$ にその値を変更します。  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  \\Templates\\Projects\\SimpleProject\\Program.cs ファイル内のファイルの内容を次のコードに置き換えます。  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace $safeprojectname$ { [Guid("$guid1$")] public class $safeprojectname$ { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
4.  SimpleProject プロジェクトをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
5.  新しい SimpleProject コンソール アプリケーションを作成します。 \(で、 **プロジェクトの種類** \] ウィンドウの \[ **SimpleProject**します。**Visual Studio にインストールされたテンプレート**, \[ **コンソール アプリケーション**.\)  
  
6.  新しく作成されたプロジェクトで Program.cs を開きます。 次のような項目が表示されます \(ファイルの GUID 値は異なります。\)。  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace Console_Application1 { [Guid("00000000-0000-0000-00000000-00000000)"] public class Console_Application1 { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
## プロジェクト プロパティ ページを作成します。  
 プロジェクトの種類のプロパティ ページを作成するには、ユーザーが表示して、テンプレートに基づくプロジェクトのプロパティを変更できるようにします。 このセクションでは、構成に依存しないプロパティ ページを作成する方法を示します。 この基本的なプロパティ ページでは、プロパティ グリッドを使用して、プロパティ ページのクラスで公開するパブリック プロパティを表示します。  
  
 クラス、プロパティ ページから、 `SettingsPage` 基本クラスです。 によって提供されるプロパティ グリッド、 `SettingsPage` クラスはほとんどのプリミティブ データ型を認識し、それらを表示する方法を認識します。  さらに、 `SettingsPage` クラスをプロジェクト ファイルのプロパティ値を保持する方法を認識します。  
  
 このセクションで作成するプロパティ ページでは、変更およびこれらのプロジェクト プロパティを保存できます。  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace します。  
  
1.  SimpleProjectPackage.cs ファイルでこれを追加 `ProvideObject` 属性を `SimpleProjectPackage` クラス。  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))] public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     これで、プロパティ ページ クラスが登録 `GeneralPropertyPage` COM で  
  
2.  SimpleProjectNode.cs ファイル内に 2 つのオーバーライドされたメソッドを追加、 `SimpleProjectNode` クラス。  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; } protected override Guid[] GetPriorityProjectDesignerPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; }  
    ```  
  
     これら両方のメソッドは、プロパティ ページの Guid の配列を返します。  GeneralPropertyPage GUID は、配列内の唯一の要素、 **プロパティ ページ** ダイアログ ボックスは 1 ページのみを表示します。  
  
3.  SimpleProject プロジェクトに GeneralPropertyPage.cs をという名前のクラス ファイルを追加します。  
  
4.  次のコードを使用してこのファイルの内容に置き換えます。  
  
    ```  
    using System; using System.Runtime.InteropServices; using Microsoft.VisualStudio; using Microsoft.VisualStudio.Project; using System.ComponentModel; namespace SimpleProject { [ComVisible(true)] [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")] public class GeneralPropertyPage : SettingsPage { private string assemblyName; private OutputType outputType; private string defaultNamespace; public GeneralPropertyPage() { this.Name = "General"; } [Category("AssemblyName")] [DisplayName("AssemblyName")] [Description("The output file holding assembly metadata.")] public string AssemblyName { get { return this.assemblyName; } } [Category("Application")] [DisplayName("OutputType")] [Description("The type of application to build.")] public OutputType OutputType { get { return this.outputType; } set { this.outputType = value; this.IsDirty = true; } } [Category("Application")] [DisplayName("DefaultNamespace")] [Description("Specifies the default namespace for added items.")] public string DefaultNamespace { get { return this.defaultNamespace; } set { this.defaultNamespace = value; this.IsDirty = true; } } protected override void BindProperties() { this.assemblyName = this.ProjectMgr.GetProjectProperty( "AssemblyName", true); this.defaultNamespace = this.ProjectMgr.GetProjectProperty( "RootNamespace", false); string outputType = this.ProjectMgr.GetProjectProperty( "OutputType", false); this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType); } protected override int ApplyChanges() { this.ProjectMgr.SetProjectProperty( "AssemblyName", this.assemblyName); this.ProjectMgr.SetProjectProperty( "OutputType", this.outputType.ToString()); this.ProjectMgr.SetProjectProperty( "RootNamespace", this.defaultNamespace); this.IsDirty = false; return VSConstants.S_OK; } } }  
    ```  
  
     `GeneralPropertyPage` クラスは、AssemblyName、OutputType、および RootNamespace は、次の 3 つのパブリック プロパティを公開します。 AssemblyName に set メソッドがあるないために、読み取り専用プロパティとして表示されます。 OutputType は列挙型の定数は、ドロップダウン リストとして表示されます。  
  
     `SettingsPage` 基本クラスが `ProjectMgr` プロパティを保持します。`BindProperties` メソッド使用 `ProjectMgr` を永続化されたプロパティの値を取得し、対応するプロパティを設定します。`ApplyChanges` メソッド使用 `ProjectMgr` プロパティの値を取得し、プロジェクト ファイルに保存します。 このプロパティは、メソッドのセットを設定 `IsDirty` を true に、プロパティを永続化する必要があることを示すためにします。  永続化は、プロジェクトまたはソリューションを保存するときに発生します。  
  
5.  SimpleProject ソリューションをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
6.  実験用インスタンスでは、新しい SimpleProject アプリケーションを作成します。  
  
7.  Visual Studio では、Visual Studio テンプレートを使用してプロジェクトを作成する、プロジェクトのファクトリを呼び出します。 コード エディターには、新しい Program.cs ファイルが開きます。  
  
8.  プロジェクト ノードを右クリックして **ソリューション エクスプ ローラー**, 、クリックして **プロパティ**します。**\[プロパティ ページ\]** ダイアログ ボックスが表示されます。  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2\_PropPage")  
  
## テスト プロジェクトのプロパティ ページ  
 ここで変更し、プロパティ値を変更するかどうかをテストできます。  
  
1.  **MyConsoleApplication プロパティ ページ** \] ダイアログ ボックスで、変更、 **DefaultNamespace** に **MyApplication**します。  
  
2.  選択、 **OutputType** プロパティ、および選択 **クラス ライブラリ**します。  
  
3.  をクリックして **適用**, 、\] をクリックし、 **OK**します。  
  
4.  再度開く、 **プロパティ ページ** \] ダイアログ ボックスし、変更内容が保存されていることを確認します。  
  
5.  Visual Studio の実験用インスタンスを閉じます。  
  
6.  実験用インスタンスをもう一度開きます。  
  
7.  再度開く、 **プロパティ ページ** \] ダイアログ ボックスし、変更内容が保存されていることを確認します。  
  
8.  Visual Studio の実験用インスタンスを閉じます。  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2\_PropPage2")