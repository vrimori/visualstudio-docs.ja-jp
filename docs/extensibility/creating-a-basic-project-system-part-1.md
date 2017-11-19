---
title: "基本的なプロジェクト システムを作成するには、パート 1 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: "47"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e61c0d681dac52e85c3854325ee20ada29d74d4c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-basic-project-system-part-1"></a>基本的なプロジェクト システムを作成するには、パート 1
Visual Studio では、プロジェクトは、開発者は、ソース コード ファイルおよびその他の資産の分類に使用するコンテナーです。 プロジェクトがソリューション内の子として表示されます、**ソリューション エクスプ ローラー**です。 プロジェクトでは、整理、ビルド、デバッグ、およびソース コードを配置および Web サービス、データベース、およびその他のリソースへの参照を作成できます。  
  
 プロジェクトは、たとえば Visual c# プロジェクトの .csproj ファイルをプロジェクト ファイルで定義されます。 独自のプロジェクト ファイル名拡張子を持つ独自のプロジェクトの種類を作成することができます。 プロジェクトの種類の詳細については、次を参照してください。[プロジェクトの種類](../extensibility/internals/project-types.md)です。  
  
> [!NOTE]
>  カスタム プロジェクトの種類と、Visual Studio を拡張する必要がある場合を強く勧めを活用すること、 [Visual Studio プロジェクト システム](https://github.com/Microsoft/VSProjectSystem)がいくつかの利点を最初からプロジェクト システムを構築します。  
>   
>  -   簡単にオンボーディングします。  基本的なプロジェクト システムもには、数万件のコード行が必要です。  数回のクリックをするには、ニーズに合わせてカスタマイズする準備がオンボーディング コストの削減 CPS を活用することです。  
> -   メンテナンスの簡素化します。  CPS を活用することによってのみ、独自のシナリオを維持する必要があります。  すべてのプロジェクト システム インフラストラクチャの保守管理を処理したとします。  
>   
>  Visual Studio の Visual Studio 2013 より前のバージョンを対象にする必要がある場合、Visual Studio 拡張機能で CPS を活用することができなきます。  場合は、このチュートリアルでは作業を開始するに適しています。  
  
 このチュートリアルでは、プロジェクト ファイル名拡張子 .myproj のあるプロジェクトの種類を作成する方法を示します。 このチュートリアルは、既存の Visual c# プロジェクト システムから借用します。  
  
> [!NOTE]
>  拡張機能プロジェクトの例については、次を参照してください。 [VSSDK のサンプル](http://aka.ms/vs2015sdksamples)です。  
  
 このチュートリアルでこれらのタスクを実行する方法について説明します。  
  
-   基本的なプロジェクトの種類を作成します。  
  
-   基本的なプロジェクト テンプレートを作成します。  
  
-   Visual Studio でプロジェクト テンプレートを登録します。  
  
-   開いてプロジェクト インスタンスを作成、**新しいプロジェクト** ダイアログ ボックスと、テンプレートを使用します。  
  
-   プロジェクト システムのプロジェクト ファクトリを作成します。  
  
-   プロジェクト システムのプロジェクト ノードを作成します。  
  
-   プロジェクト システム用のカスタム アイコンを追加します。  
  
-   基本的なテンプレート パラメーター置換を実装します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
 ソース コードをダウンロードすることも必要があります、[プロジェクト用 Managed Package Framework](http://mpfproj12.codeplex.com/)です。 作成しようとするソリューションにアクセスできる場所にファイルを抽出します。  
  
## <a name="creating-a-basic-project-type"></a>基本的なプロジェクトの種類を作成します。  
 という名前の C# の場合は、VSIX プロジェクトを作成する**SimpleProject**です。 (**ファイル、新規]、[プロジェクト**し**C# の場合、拡張性、Visual Studio パッケージ**)。 Visual Studio パッケージ プロジェクト項目テンプレートを追加する (ソリューション エクスプ ローラーでプロジェクト ノードを右クリックし **追加/新しい項目の**に移動し、 **Extensibility/Visual Studio パッケージ**)。 ファイルの名前を付けます**SimpleProjectPackage**です。  
  
## <a name="creating-a-basic-project-template"></a>基本的なプロジェクト テンプレートを作成します。  
 ここで、この新しい .myproj プロジェクトの種類を実装する VSPackage の基本を変更できます。 .Myproj プロジェクトの種類に基づいているプロジェクトを作成するには、Visual Studio が、どのファイル、リソース、および新しいプロジェクトに追加する参照を確認します。 この情報を提供するには、プロジェクト テンプレート フォルダーにプロジェクト ファイルを配置します。 ユーザーは、プロジェクトを作成する .myproj プロジェクトを使用するときに、ファイルは、新しいプロジェクトにコピーされます。  
  
#### <a name="to-create-a-basic-project-template"></a>基本的なプロジェクト テンプレートを作成するには  
  
1.  3 つのフォルダーをもう 1 つと、プロジェクトに追加: **Templates\Projects\SimpleProject**です。 (で**ソリューション エクスプ ローラー**を右クリックし、 **SimpleProject**プロジェクト ノードを指す**追加**、クリックして**新しいフォルダー**です。 フォルダーに「 `Templates`で行うことができます。 **テンプレート**フォルダー、という名前のフォルダーを追加`Projects`です。 **プロジェクト**フォルダー、という名前のフォルダーを追加`SimpleProject`)。  
  
2.  **Projects\SimpleProject**という名前のアイコン ファイルをフォルダーに追加`SimpleProject.ico`です。 クリックすると、**追加**、アイコン エディターが開きます。  
  
3.  個性的なアイコンを確認します。 このアイコンに表示されます、**新しいプロジェクト**チュートリアルの後半でダイアログ ボックス。  
  
     ![単純なプロジェクト アイコン](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  アイコンを保存してアイコン エディターを閉じます。  
  
5.  **Projects\SimpleProject**フォルダーで、追加、**クラス**という名前の項目`Program.cs`です。  
  
6.  既存のコードを次の行に置き換えます。  
  
    ```csharp  
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
    >  これは、Program.cs コードの最終形式ではありません。置換パラメーターの後の手順で処理します。 表示されるコンパイル エラーがいる限り、ファイルの**"ビルド アクション"**は**コンテンツ**をビルドして、プロジェクトを通常どおり実行することができます。  
  
1.  ファイルを保存します。  
  
2.  AssemblyInfo.cs ファイルのコピー、**プロパティ**フォルダーを**Projects\SimpleProject**フォルダーです。  
  
3.  **Projects\SimpleProject**フォルダーという XML ファイルを追加する`SimpleProject.myproj`です。  
  
    > [!NOTE]
    >  この種類のすべてのプロジェクトのファイル名拡張子は、.myproj です。 これを変更する場合は、する必要があります変更するチュートリアルで指定されているすべての場所。  
  
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
  
6.  **プロパティ**ウィンドウで、設定、**ビルド アクション**AssemblyInfo.cs、Program.cs、SimpleProject.ico、およびに SimpleProject.myproj の**コンテンツ**、およびそのを設定**VSIX に含める**プロパティ**True**です。  
  
 このプロジェクト テンプレートでは、基本的な Visual c# プロジェクトをデバッグ構成とリリース構成の両方を持つについて説明します。 プロジェクトには、2 つのソース ファイル、AssemblyInfo.cs、Program.cs、およびいくつかのアセンブリが含まれています。 参照します。 テンプレートからプロジェクトが作成されると、新しい GUID によって ProjectGuid 値が自動的に置換します。  
  
 **ソリューション エクスプ ローラー**、展開した**テンプレート**フォルダーが次のように表示されます。  
  
 テンプレート  
  
 プロジェクト  
  
 SimpleProject  
  
 AssemblyInfo.cs  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## <a name="creating-a-basic-project-factory"></a>基本的なプロジェクト ファクトリを作成します。  
 Visual Studio プロジェクト テンプレート フォルダーの場所を指定する必要があります。 これを行うには、属性をテンプレートの場所は、VSPackage をビルドするときに、システム レジストリに書き込まれるように、プロジェクト ファクトリを実装する VSPackage クラスを追加します。 まずプロジェクト ファクトリ GUID によって識別される基本的なプロジェクト ファクトリを作成します。 使用して、 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> SimpleProjectPackage クラスをプロジェクト ファクトリを接続する属性。  
  
#### <a name="to-create-a-basic-project-factory"></a>基本的なプロジェクト ファクトリを作成するには  
  
1.  コード エディターで SimpleProjectPackageGuids.cs を開きます。  
  
2.  プロジェクト ファクトリの Guid を作成 (上、**ツール** メニューのをクリックして**GUID の作成**)、か、次の例で使用します。 Guid を SimpleProjectPackageGuids クラスに追加します。 Guid は、GUID 形式と文字列の形式の両方でなければなりません。 結果のコードは次の例のようになります。  
  
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
  
3.  上部にクラスを追加**SimpleProject**という名前のフォルダー`SimpleProjectFactory.cs`です。  
  
4.  次の追加ステートメントを使用します。  
  
    ```  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  SimpleProjectFactory クラスには、Guid 属性を追加します。 属性の値は、新しいプロジェクト ファクトリの GUID です。  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 今すぐプロジェクト テンプレートを登録することができます。  
  
#### <a name="to-register-the-project-template"></a>プロジェクト テンプレートを登録するには  
  
1.  SimpleProjectPackage.cs で追加、<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>属性 SimpleProjectPackage クラスに次のようにします。  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  ソリューションをリビルドし、エラーなしにビルドされることを確認します。  
  
     プロジェクト テンプレートを登録の再構築します。  
  
 パラメーター`defaultProjectExtension`と`possibleProjectExtensions`プロジェクト ファイル名拡張子 (.myproj) に設定されます。 `projectTemplatesDirectory`パラメーターが、テンプレート フォルダーの相対パスに設定します。 、ビルド時にこのパス変換をフル ビルドされ、プロジェクト システムに登録するレジストリに追加します。  
  
## <a name="testing-the-template-registration"></a>テンプレートの登録のテスト  
 テンプレート登録に指示 Visual Studio プロジェクト テンプレート フォルダーの場所 Visual Studio は、テンプレート名とアイコンを表示できるように、**新しいプロジェクト** ダイアログ ボックス。  
  
#### <a name="to-test-the-template-registration"></a>テンプレート登録をテストするには  
  
1.  F5 キーを押して Visual Studio の実験用インスタンスのデバッグを開始します。  
  
2.  実験用インスタンスの新しく作成されたプロジェクトの種類の新しいプロジェクトを作成します。 **新しいプロジェクト**ダイアログ ボックスで、表示されるはず**SimpleProject** **にインストールされたテンプレート**です。  
  
 今すぐプロジェクト ファクトリが登録されている必要があります。 ただし、プロジェクトをまだ作成できません。 プロジェクト パッケージとプロジェクト ファクトリは連携して、作成して、プロジェクトを初期化します。  
  
## <a name="add-the-managed-package-framework-code"></a>Managed Package Framework のコードを追加します。  
 プロジェクト パッケージとプロジェクト ファクトリ間の接続を実装します。  
  
-   Managed Package Framework のソース コード ファイルをインポートします。  
  
    1.  SimpleProject プロジェクトのアンロード (で**ソリューション エクスプ ローラー**プロジェクト ノードを選択し、コンテキスト メニューをクリックして、**プロジェクトのアンロード**。) XML エディターで、プロジェクト ファイルを開くとします。  
  
    2.  プロジェクト ファイルに次のブロックを追加 (すぐ上、\<インポート > ブロック) します。 ProjectBasePath を Managed Package Framework のコードにダウンロードした ProjectBase.files ファイルの場所に設定します。 パス名に円記号を追加する必要があります。 そうしないと、プロジェクトが失敗する場合、Managed Package Framework コードを検索します。  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  パスの最後に円記号を忘れないでください。  
  
    3.  プロジェクトの再読み込みします。  
  
    4.  次のアセンブリへの参照を追加します。  
  
        -   Microsoft.VisualStudio.Designer.Interfaces (で\<VSSDK インストール > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>プロジェクト ファクトリを初期化するために  
  
1.  SimpleProjectPackage.cs ファイルに次のコードを追加`using`ステートメントです。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  派生、`SimpleProjectPackage`クラス`Microsoft.VisualStudio.Package.ProjectPackage`です。  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  プロジェクト ファクトリを登録します。 次の行を追加、`SimpleProjectPackage.Initialize`メソッド、直後`base.Initialize`です。  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  抽象プロパティを実装して`ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  SimpleProjectFactory.cs で次のコードを追加`using`後、既存のステートメント`using`ステートメントです。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  派生、`SimpleProjectFactory`クラス`ProjectFactory`です。  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  次のダミー メソッドを追加、`SimpleProjectFactory`クラスです。 以降のセクションでは、このメソッドを実装します。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  次のフィールドとコンス トラクターを追加、`SimpleProjectFactory`クラスです。 これは、`SimpleProjectPackage`参照が、プライベート フィールドにキャッシュされるので、サービス プロバイダ サイトの設定で使用できます。  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. ソリューションをリビルドし、エラーなしにビルドされることを確認します。  
  
## <a name="testing-the-project-factory-implementation"></a>テスト プロジェクト ファクトリの実装  
 プロジェクト ファクトリの実装のコンス トラクターを呼び出すかどうかをテストします。  
  
#### <a name="to-test-the-project-factory-implementation"></a>プロジェクト ファクトリの実装をテストするには  
  
1.  SimpleProjectFactory.cs ファイル内の次の行にブレークポイントを設定、`SimpleProjectFactory`コンス トラクターです。  
  
    ```  
    this.package = package;  
    ```  
  
2.  F5 キーを押して Visual Studio の実験用インスタンスを起動します。  
  
3.  実験用インスタンスには、新しいプロジェクトの作成を開始します。**新しいプロジェクト** ダイアログ ボックスで、SimpleProject プロジェクトの種類をクリックし、 **OK**です。 ブレークポイントで実行が停止します。  
  
4.  ブレークポイントを解除し、デバッグを停止します。 プロジェクト ノードをまだ作成してされていない、ため、プロジェクトの作成のコードはまだ例外をスローします。  
  
## <a name="extending-the-project-node-class"></a>プロジェクト ノードのクラスを拡張します。  
 これで、実装することができます、`SimpleProjectNode`から派生するクラス、`ProjectNode`クラスです。 `ProjectNode`基底クラスがプロジェクトの作成の次のタスクを処理します。  
  
-   プロジェクト テンプレートのファイル、SimpleProject.myproj を新しいプロジェクト フォルダーにコピーします。 入力された名に従って名前が変更、コピー、**新しいプロジェクト** ダイアログ ボックス。 `ProjectGuid`プロパティの値は、新しい GUID によって置き換えられます。  
  
-   プロジェクト テンプレートのファイル、SimpleProject.myproj の MSBuild の要素を走査し、検索`Compile`要素。 各`Compile`ターゲット ファイル、ファイルを新しいプロジェクト フォルダーにコピーします。  
  
 派生した`SimpleProjectNode`クラスはこれらのタスクを処理します。  
  
-   プロジェクトとファイル内のノードのアイコンを有効に**ソリューション エクスプ ローラー**作成または選択します。  
  
-   指定する追加のプロジェクト テンプレートのパラメーター置換を有効にします。  
  
#### <a name="to-extend-the-project-node-class"></a>プロジェクト ノードのクラスを拡張するには  
  
1.  
  
2.  という名前のクラスを追加`SimpleProjectNode.cs`です。  
  
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
  
 これは、`SimpleProjectNode`クラスの実装がこれらのオーバーライドされたメソッド。  
  
-   `ProjectGuid`をプロジェクト ファクトリ GUID が返されます。  
  
-   `ProjectType`、プロジェクトの種類のローカライズされた名前が返されます。  
  
-   `AddFileFromTemplate`、テンプレート フォルダーからコピー先のプロジェクトに選択したファイルをコピーします。 このメソッドは、後のセクションでさらに実装します。  
  
 `SimpleProjectNode`コンス トラクターと同様、`SimpleProjectFactory`コンス トラクター、キャッシュ、`SimpleProjectPackage`の後で使用するプライベート フィールドで参照します。  
  
 接続する、`SimpleProjectFactory`クラスを`SimpleProjectNode`クラス、インスタンス化して、新しい`SimpleProjectNode`で、`SimpleProjectFactory.CreateProject`メソッドし、後で使用できるプライベート フィールドにキャッシュします。  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>プロジェクトのファクトリ クラスと、ノード クラスに接続するには  
  
1.  SimpleProjectFactory.cs ファイルに次のコードを追加`using`ステートメント。  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  置換、`SimpleProjectFactory.CreateProject`方法を次のコードを使用します。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  ソリューションをリビルドし、エラーなしにビルドされることを確認します。  
  
## <a name="testing-the-project-node-class"></a>テスト プロジェクトのノード クラス  
 プロジェクトの階層を作成するかどうかを表示する、プロジェクト ファクトリをテストします。  
  
#### <a name="to-test-the-project-node-class"></a>プロジェクト ノードのクラスをテストするには  
  
1.  F5 キーを押してデバッグを開始します。 実験用インスタンスの新しい SimpleProject を作成します。  
  
2.  Visual Studio では、プロジェクトを作成する、プロジェクト ファクトリを呼び出す必要があります。  
  
3.  Visual Studio の実験用インスタンスを終了します。  
  
## <a name="adding-a-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンを追加します。  
 前のセクションで、プロジェクト ノードのアイコンは、既定のアイコンです。 カスタム アイコンに変更することができます。  
  
#### <a name="to-add-a-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンを追加するには  
  
1.  **リソース**フォルダー、SimpleProjectNode.bmp をという名前のビットマップ ファイルを追加します。  
  
2.  **プロパティ**windows では、16 x 16 ピクセルにビットマップを減らします。 印象的なビットマップを作成します。  
  
     ![単純なプロジェクト Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  **プロパティ**ウィンドウで、変更、**ビルド アクション**にビットマップの**埋め込まれたリソース**です。  
  
4.  次のコードを追加で SimpleProjectNode.cs、`using`ステートメント。  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  次の静的フィールドとコンス トラクターを追加、`SimpleProjectNode`クラスです。  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  先頭に次のプロパティを追加、`SimpleProjectNode`クラスです。  
  
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
  
 構築時に静的、`SimpleProjectNode`アセンブリのマニフェスト リソースから、プロジェクト ノードのビットマップを取得し、後で使用できるプライベート フィールドにキャッシュします。 構文に注意してください、<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>イメージのパス。 アセンブリに埋め込まれたマニフェスト リソースの名前を表示するを使用して、<xref:System.Reflection.Assembly.GetManifestResourceNames%2A>メソッドです。 このメソッドを適用すると、`SimpleProject`アセンブリ、結果は、次のようにする必要があります。  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 インスタンスの構築時に、`ProjectNode`基底クラスが埋め込まれた一般的に使用される 16 x 16 のビットマップを Resources\imagelis.bmp で Resources.imagelis.bmp を読み込みます。 このビットマップのリストが使用される`SimpleProjectNode`ImageHandler.ImageList として。 `SimpleProjectNode`一覧に、プロジェクト ノードのビットマップを追加します。 イメージ リストには、プロジェクト ノードのビットマップのオフセットは、パブリックの値として後で使用できるキャッシュ`ImageIndex`プロパティです。 Visual Studio では、このプロパティを使用して、プロジェクト ノードのアイコンとして表示するには、どのビットマップを調べます。  
  
## <a name="testing-the-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンのテスト  
 カスタム プロジェクト ノードのアイコンがプロジェクトの階層を作成するかどうかを表示する、プロジェクト ファクトリをテストします。  
  
#### <a name="to-test-the-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンをテストするには  
  
1.  デバッグを開始し、実験用インスタンスで新しい SimpleProject を作成します。  
  
2.  プロジェクトで、新しく作成されたプロジェクト ノードのアイコンとして SimpleProjectNode.bmp を使用することを確認します。  
  
     ![新しいプロジェクト ノードを単純なプロジェクト](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
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
  
     $NameSpace$ および $className$ テンプレート パラメーターに、新しい値がないことに注意してください。 次のセクションでテンプレート パラメーター置換を実装する方法を学習します。  
  
## <a name="substituting-template-parameters"></a>テンプレート パラメーターの置換  
 前のセクションで登録したプロジェクト テンプレートで Visual Studio を使用して、`ProvideProjectFactory`属性。 この方法で、テンプレート フォルダーのパスを登録することができますをオーバーライドし、展開の基本的なテンプレート パラメーター置換を有効にする、`ProjectNode.AddFileFromTemplate`クラスです。 詳細については、次を参照してください。[新しいプロジェクトの生成: 短縮、パート 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)です。  
  
 今すぐに交換用コードを追加、`AddFileFromTemplate`クラスです。  
  
#### <a name="to-substitute-template-parameters"></a>テンプレート パラメーターの代わりに  
  
1.  SimpleProjectNode.cs ファイルに次のコードを追加`using`ステートメントです。  
  
    ```  
    using System.IO;  
    ```  
  
2.  置換、`AddFileFromTemplate`方法を次のコードを使用します。  
  
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
  
3.  直後に、メソッドにブレークポイントを設定、`className`代入ステートメント。  
  
 代入ステートメントは、名前空間とクラスの新しい名前の適切な値を決定します。 2 つ`ProjectNode.FileTemplateProcessor.AddReplace`メソッドの呼び出しは、これらの新しい値を使用して、対応するテンプレート パラメーターの値を置き換えます。  
  
## <a name="testing-the-template-parameter-substitution"></a>テンプレート パラメーター置換のテスト  
 テンプレート パラメーター置換をテストできます。  
  
#### <a name="to-test-the-template-parameter-substitution"></a>テンプレート パラメーターの置換をテストするには  
  
1.  デバッグを開始し、実験用インスタンスで新しい SimpleProject を作成します。  
  
2.  内のブレークポイントで実行が停止、`AddFileFromTemplate`メソッドです。  
  
3.  値を調べ、`nameSpace`と`className`パラメーター。  
  
    -   `nameSpace`値を指定された、 \<RootNamespace > \Templates\Projects\SimpleProject\SimpleProject.myproj プロジェクトのテンプレート ファイル内の要素。 この場合、値が"MyRootNamespace"  
  
    -   `className`ファイル名拡張子の付かない、クラスのソース ファイル名の値を指定します。 この場合、コピー先のフォルダーにコピーする最初のファイルは、AssemblyInfo.cs です。そのため、クラス名の値は、"AssemblyInfo"です。  
  
4.  ブレークポイントを削除し、実行を継続する場合は F5 キーを押します。  
  
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
  
     名前空間が"MyRootNamespace"こと、および、クラス名が「プログラム」ことに注意してください。  
  
6.  プロジェクトのデバッグを開始します。 コンパイル、実行、および「VSX こんにちは!」を表示する必要があります、新しいプロジェクト コンソール ウィンドウに表示します。  
  
     ![単純なプロジェクト コマンド](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 おめでとうございます!  マネージ プロジェクトの基本的なシステムを実装しています。