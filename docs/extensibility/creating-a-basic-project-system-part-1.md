---
title: "基本的なプロジェクト システム、第 1 部を作成します。 | Microsoft Docs"
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
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 47
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 47
---
# 基本的なプロジェクト システム、第 1 部を作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio では、プロジェクトは、開発者は、ソース コード ファイルおよびその他のアセットの分類に使用するコンテナーです。 プロジェクトがソリューション内の子として表示されます、 **ソリューション エクスプ ローラー**します。 プロジェクトでは、整理、ビルド、デバッグ、およびソース コードを配置、および Web サービス、データベース、およびその他のリソースへの参照を作成できます。  
  
 プロジェクトは、たとえば Visual c\# プロジェクトの .csproj ファイルをプロジェクト ファイルで定義されます。 独自のプロジェクト ファイル名拡張子を持つ独自のプロジェクトの種類を作成することができます。 プロジェクトの種類の詳細については、次を参照してください。 [プロジェクトの種類](../extensibility/internals/project-types.md)します。  
  
> [!NOTE]
>  カスタムのプロジェクトの種類に Visual Studio を拡張する場合は、強くお勧めを活用すること、 [Visual Studio プロジェクト システム](https://github.com/Microsoft/VSProjectSystem) を持つさまざまなプロジェクト システムを一から構築に比べて利点があります。  
>   
>  -   簡単にオンボーディングします。  基本的なプロジェクト システムではさらには、数万の行のコードが必要です。  前に、お客様のニーズに合わせてカスタマイズする準備ができたら、数回のクリックにオンボーディング コストを削減する CPS を活用することです。  
> -   メンテナンスを容易にします。  CPS を活用することでのみ、実際のシナリオを維持する必要があります。  すべてのプロジェクト システム インフラストラクチャの保守管理が処理されます。  
>   
>  Visual Studio 2013 よりも古い Visual Studio のバージョンを対象にする場合は、Visual Studio 拡張機能で CPS を活用することができなきます。  場合は、このチュートリアルでは開始することをお勧めします。  
  
 このチュートリアルでは、プロジェクト ファイル名拡張子 .myproj のあるプロジェクトの種類を作成する方法を示します。 このチュートリアルでは、既存の Visual c\# プロジェクト システムから借用します。  
  
> [!NOTE]
>  エンド ツー エンドのサンプルの完全な言語のプロジェクト システムには、\[IronPython サンプルの詳細情報を参照してください。 [VSSDK のサンプル](../misc/vssdk-samples.md)します。  
  
 このチュートリアルでは、これらのタスクを実行する方法について説明します。  
  
-   基本的なプロジェクトの種類を作成します。  
  
-   基本的なプロジェクト テンプレートを作成します。  
  
-   Visual Studio でプロジェクト テンプレートを登録します。  
  
-   開くことで、プロジェクトのインスタンスを作成、 **新しいプロジェクト** \] ダイアログ ボックスと、テンプレートを使用します。  
  
-   プロジェクト システムのプロジェクト ファクトリを作成します。  
  
-   プロジェクト システムのプロジェクト ノードを作成します。  
  
-   プロジェクト システム用のカスタム アイコンを追加します。  
  
-   基本的なテンプレート パラメーター置換を実装します。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
 ソース コードをダウンロードすることも必要があります、 [のプロジェクトのパッケージの管理フレームワーク](http://mpfproj12.codeplex.com/)します。 作成しようとするソリューションにアクセスできる場所にファイルを抽出します。  
  
## 基本的なプロジェクトの種類を作成します。  
 という名前の C\# の場合は、VSIX プロジェクトを作成する **SimpleProject**します。 \(**ファイル\]、\[新規\]、\[プロジェクト** し **C\# の場合、拡張性、Visual Studio パッケージ**\)。 Visual Studio パッケージ プロジェクト項目テンプレートを追加する \(ソリューション エクスプ ローラーで、プロジェクト ノードを右クリックし \[ **追加\/\[新しい項目の**, に移動し、 **拡張\/Visual Studio パッケージ**\)。 ファイルに名前を **SimpleProjectPackage**します。  
  
## 基本的なプロジェクト テンプレートを作成します。  
 これで、この新しい .myproj プロジェクトの種類を実装する VSPackage の基本を変更できます。 .Myproj プロジェクトの種類に基づいているプロジェクトを作成するには、Visual Studio はどのファイル、リソース、および新しいプロジェクトに追加する参照を知るには。 この情報を提供するには、プロジェクトのテンプレート フォルダーにプロジェクト ファイルを配置します。 ユーザーは、プロジェクトを作成する .myproj プロジェクトを使用するときに、ファイルは、新しいプロジェクトにコピーされます。  
  
#### 基本的なプロジェクト テンプレートを作成するには  
  
1.  3 つのフォルダーを他の下に 1 つと、プロジェクトに追加: **Templates\\Projects\\SimpleProject**します。 \(で **ソリューション エクスプ ローラー**, を右クリックし、 **SimpleProject** プロジェクト ノードを指す **追加**, 、\] をクリックし、 **新しいフォルダー**します。 そのフォルダーに名前 `Templates`します。**テンプレート** フォルダー、という名前のフォルダーを追加 `Projects`します。**プロジェクト** フォルダー、という名前のフォルダーを追加 `SimpleProject`.\)  
  
2.  **Projects\\SimpleProject** という名前のアイコン ファイルをフォルダーに追加 `SimpleProject.ico`します。 クリックすると、 **追加**, 、アイコン エディターが開きます。  
  
3.  独自のアイコンを確認します。 このアイコンに表示されます、 **新しいプロジェクト** チュートリアルの後半でダイアログ ボックス。  
  
     ![単純なプロジェクト アイコン](~/docs/extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  アイコンを保存し、アイコン エディターを閉じます。  
  
5.  **Projects\\SimpleProject** \] フォルダーを追加、 **クラス** という項目 `Program.cs`します。  
  
6.  既存のコードを次の行に置き換えます。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
    > [!IMPORTANT]
    >  これは、Program.cs のコードの最終形式ではありません。置換パラメーターは、後の手順で対処されます。 表示されるコンパイル エラーと同じくらい、ファイルの **"ビルド アクション"** は **コンテンツ**, 、ビルドして、プロジェクトを通常どおり実行できる必要があります。  
  
1.  ファイルを保存します。  
  
2.  AssemblyInfo.cs ファイルのコピー、 **プロパティ** フォルダーを **Projects\\SimpleProject** フォルダーです。  
  
3.  **Projects\\SimpleProject** フォルダーという XML ファイルを追加する `SimpleProject.myproj`です。  
  
    > [!NOTE]
    >  この種類のすべてのプロジェクトのファイル名拡張子は、.myproj です。 変更する場合をあらゆる場所で、チュートリアルに記載されて、変更する必要があります。  
  
4.  次の行で、既存のコンテンツを置き換えます。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid></ProjectGuid>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>MyRootNamespace</RootNamespace>  
        <AssemblyName>MyAssemblyName</AssemblyName>  
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        <DebugSymbols>true</DebugSymbols>  
        <OutputPath>bin\Debug\</OutputPath>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
        <DebugSymbols>false</DebugSymbols>  
        <OutputPath>bin\Release\</OutputPath>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="mscorlib" />  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="AssemblyInfo.cs">  
          <SubType>Code</SubType>  
        </Compile>  
        <Compile Include="Program.cs">  
          <SubType>Code</SubType>  
        </Compile>  
      </ItemGroup>  
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
    </Project>  
    ```  
  
5.  ファイルを保存します。  
  
6.  **プロパティ** ウィンドウで、設定、 **ビルド アクション** AssemblyInfo.cs、Program.cs、SimpleProject.ico、およびに SimpleProject.myproj の **コンテンツ**, 、設定とその **\[VSIX に含める** プロパティを **True**します。  
  
 このプロジェクト テンプレートでは、基本的な Visual c\# プロジェクトをデバッグ構成とリリース構成の両方を持つについて説明します。 プロジェクトには、2 つのソース ファイル、AssemblyInfo.cs、Program.cs、およびいくつかのアセンブリが含まれています。 参照します。 テンプレートからプロジェクトが作成されると、新しい GUID を使用して ProjectGuid 値が自動的に置換します。  
  
 **ソリューション エクスプ ローラー**, 、展開された **テンプレート** フォルダーに次のようになります。  
  
 テンプレート  
  
 プロジェクト  
  
 SimpleProject  
  
 AssemblyInfo.cs  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## 基本的なプロジェクト ファクトリを作成します。  
 Visual Studio に、プロジェクト テンプレート フォルダーの場所を指示する必要があります。 これを行うには、テンプレートの場所は、VSPackage をビルドするときに、システム レジストリに書き込まれるように、プロジェクトのファクトリを実装する VSPackage クラスに属性を追加します。 プロジェクト ファクトリ GUID によって識別される基本的なプロジェクト ファクトリを作成して開始します。 使用して、 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> SimpleProjectPackage クラスに、プロジェクトのファクトリを接続するための属性です。  
  
#### 基本的なプロジェクト ファクトリを作成するには  
  
1.  コード エディターで SimpleProjectPackageGuids.cs を開きます。  
  
2.  プロジェクト ファクトリの Guid を作成 \(上、 **ツール** \] メニューのをクリックして **GUID の作成**\)、または次の例では 1 つを使用します。 Guid を SimpleProjectPackageGuids クラスに追加します。 Guid は、GUID の形式と文字列の形式の両方でなければなりません。 その結果のコードは次の例のようになります。  
  
    ```  
    static class SimpleProjectPackageGuids  
    {  
        public const string guidSimpleProjectPkgString =   
            "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
        public const string guidSimpleProjectCmdSetString =   
            "72c23e1d-f389-410a-b5f1-c938303f1391";  
        public const string guidSimpleProjectFactoryString =   
            "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
        public static readonly Guid guidSimpleProjectCmdSet =   
            new Guid(guidSimpleProjectCmdSetString);  
        public static readonly Guid guidSimpleProjectFactory =   
            new Guid(guidSimpleProjectFactoryString);  
    }  
    ```  
  
3.  上部にクラスを追加 **SimpleProject** という名前のフォルダー `SimpleProjectFactory.cs`します。  
  
4.  次の追加のステートメントを使用します。  
  
    ```  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  SimpleProjectFactory クラスには、Guid 属性を追加します。 属性の値は、新しいプロジェクトのファクトリの GUID です。  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 これで、プロジェクト テンプレートを登録できます。  
  
#### プロジェクト テンプレートを登録するには  
  
1.  SimpleProjectPackage.cs で追加、 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 属性 SimpleProjectPackage クラスを次のようにします。  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  ソリューションをリビルドし、エラーを発生させずにビルドされることを確認します。  
  
     プロジェクト テンプレートを登録の再構築します。  
  
 パラメーター `defaultProjectExtension` と `possibleProjectExtensions` プロジェクト ファイル名拡張子 \(.myproj\) に設定されます。`projectTemplatesDirectory` パラメーターがテンプレート フォルダーの相対パスに設定します。 ビルド中には、このパスを完全なビルドに変換し、プロジェクト システムを登録するためにレジストリに追加して行います。  
  
## テンプレート登録のテスト  
 テンプレート登録通知 Visual Studio プロジェクト テンプレート フォルダーの場所 Visual Studio は、テンプレートの名前とアイコンを表示できるように、 **新しいプロジェクト** \] ダイアログ ボックス。  
  
#### テンプレート登録をテストするには  
  
1.  F5 キーを押して、Visual Studio の実験用インスタンスのデバッグを開始します。  
  
2.  実験用インスタンスでは、新しく作成されたプロジェクトの種類の新しいプロジェクトを作成します。**新しいプロジェクト** \] ダイアログ ボックスが表示されます **SimpleProject** \[ **にインストールされたテンプレート**します。  
  
 登録されているプロジェクト ファクトリがあるようになりました。 ただし、プロジェクトをまだ作成できません。 プロジェクトのパッケージとプロジェクト ファクトリは連携してを作成し、プロジェクトを初期化します。  
  
## パッケージのフレームワークをマネージ コードを追加します。  
 プロジェクトのパッケージとプロジェクトの出荷時の間の接続を実装します。  
  
-   パッケージの管理フレームワークのソース コード ファイルをインポートします。  
  
    1.  SimpleProject プロジェクトをアンロード \(で **ソリューション エクスプ ローラー**, プロジェクト ノードを選択し、コンテキスト メニューをクリックして、 **プロジェクトのアンロード**.\) XML エディターでプロジェクト ファイルを開きます.  
  
    2.  プロジェクト ファイル \(\< Import \> ブロック\) のすぐ上に、次のブロックを追加します。 ダウンロードしたパッケージ Framework のマネージ コードで ProjectBase.files ファイルの場所を ProjectBasePath を設定します。 パス名に円記号を追加する必要があります。 そうしないと、プロジェクトがパッケージ フレームワークのマネージ コードを検索に失敗します。  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  パスの末尾に円記号を忘れないでください。  
  
    3.  プロジェクトの再読み込みします。  
  
    4.  次のアセンブリへの参照を追加します。  
  
        -   \< VSSDK インストール \> \\VisualStudioIntegration\\Common\\Assemblies\\v2.0\) の「Microsoft.VisualStudio.Designer.Interfaces  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### プロジェクトのファクトリを初期化するには  
  
1.  SimpleProjectPackage.cs ファイルに次のコードを追加 `using` ステートメントです。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  派生、 `SimpleProjectPackage` クラスからの `Microsoft.VisualStudio.Package.ProjectPackage`です。  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  プロジェクトのファクトリを登録します。 次の行を追加、 `SimpleProjectPackage.Initialize` メソッド、直後に `base.Initialize`します。  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  抽象プロパティを実装 `ProductUserContext`:  
  
    ```c#  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  SimpleProjectFactory.cs で次のコードを追加 `using` 後、既存のステートメント `using` ステートメントです。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  派生、 `SimpleProjectFactory` クラスからの `ProjectFactory`です。  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  次のダミー メソッドを追加、 `SimpleProjectFactory` クラスです。 後のセクションでは、このメソッドを実装します。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  次のフィールドとコンス トラクターを追加、 `SimpleProjectFactory` クラスです。 これは、 `SimpleProjectPackage` 参照がプライベート フィールドにキャッシュされるので、サービス プロバイダ サイトの設定に使用できます。  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. ソリューションをリビルドし、エラーを発生させずにビルドされることを確認します。  
  
## プロジェクトのファクトリの実装をテストします。  
 プロジェクト ファクトリの実装のコンス トラクターを呼び出すかどうかをテストします。  
  
#### プロジェクトのファクトリの実装をテストするには  
  
1.  SimpleProjectFactory.cs ファイルでは、次の行にブレークポイントを設定、 `SimpleProjectFactory` コンス トラクターです。  
  
    ```  
    this.package = package;  
    ```  
  
2.  F5 キーを押して、Visual Studio の実験用インスタンスを起動します。  
  
3.  実験用インスタンスで新しいプロジェクトを作成を開始します。 **新しいプロジェクト** ダイアログ ボックスで、SimpleProject を選択し、プロジェクトの種類をクリックし、 **OK**します。 ブレークポイントで実行が停止します。  
  
4.  ブレークポイントをクリアし、デバッグを停止します。 まだ作成していないプロジェクト ノードので、プロジェクトの作成コードは引き続き例外をスローします。  
  
## プロジェクト ノードのクラスを拡張します。  
 実装することができますので、 `SimpleProjectNode` から派生したクラス、 `ProjectNode` クラスです。`ProjectNode` 基本クラスがプロジェクトの作成は、次のタスクを処理します。  
  
-   プロジェクトのテンプレート ファイル SimpleProject.myproj を新しいプロジェクト フォルダーにコピーします。 入力された名に従って名前が変更、コピー、 **新しいプロジェクト** \] ダイアログ ボックス。`ProjectGuid` 新しい GUID を使用してプロパティの値が置き換えられます。  
  
-   プロジェクトのテンプレート ファイル、SimpleProject.myproj の MSBuild の要素を走査しを探します `Compile` 要素。 各 `Compile` ターゲット ファイル、ファイルを新しいプロジェクト フォルダーにコピーします。  
  
 派生 `SimpleProjectNode` クラスは、これらのタスクを処理します。  
  
-   により、プロジェクトとファイルのノードでのアイコン **ソリューション エクスプ ローラー** 作成または選択します。  
  
-   指定する追加のプロジェクト テンプレートのパラメーター置換を有効にします。  
  
#### プロジェクト ノードのクラスを拡張するには  
  
1.  
  
2.  という名前のクラスを追加 `SimpleProjectNode.cs`します。  
  
3.  既存のコードを次のコードに置き換えます。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Project;  
  
    namespace SimpleProject  
    {  
        public class SimpleProjectNode : ProjectNode  
        {  
            private SimpleProjectPackage package;  
  
            public SimpleProjectNode(SimpleProjectPackage package)  
            {  
                this.package = package;  
            }  
            public override Guid ProjectGuid  
            {  
                get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
            }  
            public override string ProjectType  
            {  
                get { return "SimpleProjectType"; }  
            }  
  
            public override void AddFileFromTemplate(  
                string source, string target)  
            {  
                this.FileTemplateProcessor.UntokenFile(source, target);  
                this.FileTemplateProcessor.Reset();  
            }  
        }  
    }  
    ```  
  
 これは、 `SimpleProjectNode` クラスの実装がこれらのメソッドをオーバーライドします。  
  
-   `ProjectGuid`, 、プロジェクトの工場出荷時の GUID が返されます。  
  
-   `ProjectType`, で、プロジェクトの種類のローカライズされた名前が返されます。  
  
-   `AddFileFromTemplate`, 、選択したファイルをテンプレート フォルダーからコピー先のプロジェクトにコピーします。 このメソッドは、後のセクションでさらに実装されます。  
  
 `SimpleProjectNode` コンス トラクターと同様に、 `SimpleProjectFactory` コンス トラクターは、キャッシュ、 `SimpleProjectPackage` の後で使用するプライベート フィールドで参照します。  
  
 接続する、 `SimpleProjectFactory` クラスを `SimpleProjectNode` クラスをインスタンス化して、新しい `SimpleProjectNode` で、 `SimpleProjectFactory.CreateProject` メソッドし、後で使用できるプライベート フィールドにキャッシュします。  
  
#### プロジェクトのファクトリ クラスとノードのクラスを接続するには  
  
1.  SimpleProjectFactory.cs ファイルに次のコードを追加 `using` ステートメント。  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  置き換える、 `SimpleProjectFactory.CreateProject` メソッドを次のコードを使用しています。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  ソリューションをリビルドし、エラーを発生させずにビルドされることを確認します。  
  
## テスト プロジェクトのノード クラス  
 プロジェクトの階層を作成するかどうかを確認、プロジェクトのファクトリをテストします。  
  
#### プロジェクト ノードのクラスをテストするには  
  
1.  F5 キーを押してデバッグを開始します。 実験用インスタンスでは、新しい SimpleProject を作成します。  
  
2.  Visual Studio では、プロジェクトを作成する、プロジェクトのファクトリを呼び出す必要があります。  
  
3.  Visual Studio の実験用インスタンスを終了します。  
  
## カスタムのプロジェクト ノードのアイコンの追加  
 前のセクションで、プロジェクト ノードのアイコンは、既定のアイコンです。 カスタム アイコンに変更することができます。  
  
#### カスタムのプロジェクト ノードのアイコンを追加するには  
  
1.  **リソース** フォルダー、SimpleProjectNode.bmp をという名前のビットマップ ファイルを追加します。  
  
2.  **プロパティ** windows では、16 x 16 ピクセルにビットマップを削減します。 独自のビットマップを確認します。  
  
     ![単純なプロジェクト Comm](~/docs/extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  **プロパティ** ウィンドウで、変更、 **ビルド アクション** にビットマップの **埋め込まれたリソース**します。  
  
4.  次のコードを追加で SimpleProjectNode.cs、 `using` ステートメント。  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  次の静的フィールドとコンス トラクターを追加、 `SimpleProjectNode` クラスです。  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  先頭に次のプロパティを追加、 `SimpleProjectNode` クラスです。  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  インスタンス コンス トラクターを次のコードに置き換えます。  
  
    ```  
    public SimpleProjectNode(SimpleProjectPackage package)  
    {  
        this.package = package;  
  
        imageIndex = this.ImageHandler.ImageList.Images.Count;  
  
        foreach (Image img in imageList.Images)  
        {  
            this.ImageHandler.AddImage(img);  
        }  
    }  
    ```  
  
 構築時に静的、 `SimpleProjectNode` アセンブリ マニフェストのリソースから、プロジェクト ノードのビットマップを取得し、後で使用できるプライベート フィールドにキャッシュします。 構文に注意してください、 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> イメージへのパス。 アセンブリに埋め込まれているマニフェスト リソースの名前を表示するを使用して、 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> メソッドです。 このメソッドを適用した場合、 `SimpleProject` アセンブリ、結果は、次のようにする必要があります。  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 インスタンスの構築中に、 `ProjectNode` 基本クラスが Resources\\imagelis.bmp から一般的に使用される埋め込みの 16 x 16 ビットマップで Resources.imagelis.bmp を読み込みます。 利用できる、このビットマップ一覧 `SimpleProjectNode` ImageHandler.ImageList として。`SimpleProjectNode` プロジェクト ノードのビットマップを一覧に追加します。 イメージ リストには、プロジェクト ノードのビットマップのオフセットは、public の値として後で使用する、キャッシュ `ImageIndex` プロパティです。 Visual Studio では、このプロパティを使用して、プロジェクト ノードのアイコンとして表示するには、どのビットマップを調べます。  
  
## カスタムのプロジェクト ノードのアイコンのテスト  
 テスト プロジェクト工場に、カスタムのプロジェクト ノードのアイコンがプロジェクトの階層を作成するかどうかを確認してください。  
  
#### カスタムのプロジェクト ノードのアイコンをテストするには  
  
1.  デバッグを開始し、実験用インスタンスで新しい SimpleProject を作成します。  
  
2.  新しく作成されたプロジェクトで、SimpleProjectNode.bmp がプロジェクト ノードのアイコンとして使用されることに注意してください。  
  
     ![単純なプロジェクト New Project ノード](~/docs/extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  コード エディターで、Program.cs を開きます。 次のコードのようなソース コードが表示されます。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     $NameSpace$ と $className$ テンプレート パラメーターに、新しい値がないことに注意してください。 次のセクションでテンプレート パラメーター置換を実装する方法を学習します。  
  
## テンプレート パラメーターの置換  
 前のセクションで登録したプロジェクト テンプレートで Visual Studio を使用して、 `ProvideProjectFactory` 属性です。 オーバーライドし、展開する基本的なテンプレート パラメーター置換を有効にするこの方法でテンプレート フォルダーのパスを登録することができます、 `ProjectNode.AddFileFromTemplate` クラスです。 詳細については、「[新しいプロジェクトの生成: 実際のところ、第 2 部します。](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md)」を参照してください。  
  
 交換用のコードを追加、 `AddFileFromTemplate` クラスです。  
  
#### テンプレート パラメーター値  
  
1.  SimpleProjectNode.cs ファイルに次のコードを追加 `using` ステートメントです。  
  
    ```  
    using System.IO;  
    ```  
  
2.  置き換える、 `AddFileFromTemplate` メソッドを次のコードを使用しています。  
  
    ```  
    public override void AddFileFromTemplate(  
        string source, string target)  
    {  
        string nameSpace =   
            this.FileTemplateProcessor.GetFileNamespace(target, this);  
        string className = Path.GetFileNameWithoutExtension(target);  
  
        this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);  
        this.FileTemplateProcessor.AddReplace("$className$", className);  
  
        this.FileTemplateProcessor.UntokenFile(source, target);  
        this.FileTemplateProcessor.Reset();  
    }  
    ```  
  
3.  直後に、メソッドにブレークポイントを設定、 `className` 代入ステートメント。  
  
 代入ステートメントは、名前空間と新しいクラス名の妥当な値を決定します。 2 つ `ProjectNode.FileTemplateProcessor.AddReplace` メソッドの呼び出しは、これらの新しい値を使用して、対応するテンプレート パラメーターの値を置き換えます。  
  
## テンプレート パラメーター置換のテスト  
 テンプレート パラメーター置換をテストできます。  
  
#### テンプレート パラメーター置換をテストするには  
  
1.  デバッグを開始し、実験用インスタンスで新しい SimpleProject を作成します。  
  
2.  内のブレークポイントで実行が停止、 `AddFileFromTemplate` メソッドです。  
  
3.  値を調べ、 `nameSpace` と `className` パラメーター。  
  
    -   `nameSpace` \\Templates\\Projects\\SimpleProject\\SimpleProject.myproj プロジェクト テンプレート ファイルで \< RootNamespace \> 要素の値を指定します。 この場合、値が"MyRootNamespace"  
  
    -   `className` ファイル名拡張子の付かない、クラスのソース ファイル名の値を指定します。 この場合、コピー先のフォルダーにコピーされる最初のファイルは、AssemblyInfo.cs です。そのため、クラス名の値は、"AssemblyInfo"です。  
  
4.  ブレークポイントを削除し、f5 キーを押して実行を続行します。  
  
     Visual Studio では、プロジェクトの作成を完了する必要があります。  
  
5.  コード エディターで、Program.cs を開きます。 次のコードのようなソース コードが表示されます。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace MyRootNamespace  
    {  
        public class Program  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     名前空間が"MyRootNamespace"こと、およびクラス名は、「プログラム」ことに注意してください。  
  
6.  プロジェクトのデバッグを開始します。 新しいプロジェクトはコンパイル、実行、および「VSX こんにちは\!\!\!」と表示 コンソール ウィンドウ。  
  
     ![単純なプロジェクト コマンド](~/docs/extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 おめでとうございます\!  マネージ プロジェクトは、基本的なシステムを実装しました。