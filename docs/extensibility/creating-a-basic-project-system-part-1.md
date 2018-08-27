---
title: 基本的なプロジェクト システムを作成するには、パート 1 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2343218da765ad8bb9a10d585001c5f3321a0137
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902400"
---
# <a name="create-a-basic-project-system-part-1"></a>基本的なプロジェクト システム、第 1 部を作成します。
Visual Studio では、プロジェクトは、開発者は、ソース コード ファイルおよびその他の資産の分類に使用するコンテナーです。 プロジェクトがソリューション内の子として表示されます、**ソリューション エクスプ ローラー**します。 プロジェクトでは、整理、ビルド、デバッグ、およびソース コードをデプロイおよび Web サービス、データベース、およびその他のリソースへの参照を作成できます。  
  
 たとえばプロジェクトをプロジェクト ファイルで定義された、 *.csproj* Visual c# プロジェクトのファイル。 独自のプロジェクト ファイル名拡張子を持つ独自のプロジェクトの種類を作成することができます。 プロジェクトの種類の詳細については、次を参照してください。[プロジェクトの種類](../extensibility/internals/project-types.md)します。  
  
> [!NOTE]
>  カスタムのプロジェクトの種類の Visual Studio を拡張する必要がある場合強くお勧めしますを活用すること、 [Visual Studio プロジェクト システム](https://github.com/Microsoft/VSProjectSystem)(VSP) を持つさまざまなプロジェクト システムを一から構築に比べて利点があります。  
>   
>  -  簡単にオンボードします。  基本的なプロジェクト システムではさらには、数万行のコードの必要があります。  前に、お客様のニーズに合わせてカスタマイズする準備が整ったら、ほんの数回のクリックにオンボード コストを削減する VSP を活用すること。  
>  -  メンテナンスを容易にします。  VSP を活用することによってのみ、独自のシナリオを維持する必要があります。  すべてのプロジェクト システム インフラストラクチャの保守管理を処理します。  
>   
>  Visual Studio の Visual Studio 2013 より前のバージョンをターゲットする必要がある場合、Visual Studio 拡張機能で VSP を活用することができなきます。  場合は、このチュートリアルでは開始することをお勧めします。  
  
 このチュートリアルは、プロジェクトのファイル名拡張子を持つプロジェクトの種類を作成する方法を示します *.myproj*します。 このチュートリアルでは既存の Visual c# プロジェクト システムを利用します。  
  
> [!NOTE]
>  拡張機能プロジェクトの例については、次を参照してください。 [VSSDK のサンプル](http://aka.ms/vs2015sdksamples)します。  
  
 このチュートリアルでは、これらのタスクを実行する方法について説明します。  
  
-   基本的なプロジェクトの種類を作成します。  
  
-   基本的なプロジェクト テンプレートを作成します。  
  
-   Visual Studio でプロジェクト テンプレートを登録します。  
  
-   開いてプロジェクト インスタンスを作成、**新しいプロジェクト** ダイアログ ボックスとし、テンプレートを使用します。  
  
-   プロジェクト システムのためのプロジェクト ファクトリを作成します。  
  
-   プロジェクト システムのプロジェクト ノードを作成します。  
  
-   プロジェクト システムのカスタム アイコンを追加します。  
  
-   基本的なテンプレート パラメーターの置換を実装します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
 ソース コードをダウンロードすることも必要があります、[プロジェクト用 Managed Package Framework](https://github.com/tunnelvisionlabs/MPFProj10)します。 作成しようとするソリューションにアクセスできる場所にファイルを抽出します。  
  
## <a name="create-a-basic-project-type"></a>基本的なプロジェクトの種類を作成します。  
 という名前の c# VSIX プロジェクトを作成する**SimpleProject**します。 (**ファイル** > **新しい** > **プロジェクト**し**Visual c#**  >  **機能拡張** > **VSIX プロジェクト**)。 Visual Studio パッケージ プロジェクト項目テンプレートを追加する (上、**ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**、順に移動**拡張** > **Visual Studio パッケージ**)。 ファイルに名前を*SimpleProjectPackage*します。  
  
## <a name="creating-a-basic-project-template"></a>基本的なプロジェクト テンプレートを作成します。  
 ここで、この基本的な VSPackage に、新しい実装を変更できます *.myproj*プロジェクトの種類。 基づくプロジェクトを作成する、 *.myproj* Visual Studio がどのファイル、リソース、および新しいプロジェクトに追加する参照を把握するにはプロジェクトの種類。 この情報を提供するには、プロジェクトのテンプレート フォルダーにプロジェクト ファイルを配置します。 ユーザーが使用する場合、 *.myproj*プロジェクトを作成するプロジェクトで、新しいプロジェクトにファイルがコピーされます。  
  
### <a name="to-create-a-basic-project-template"></a>基本的なプロジェクト テンプレートを作成するには  
  
1.  3 つのフォルダーを他のいずれかと、プロジェクトに追加: *Templates\Projects\SimpleProject*します。 (で**ソリューション エクスプ ローラー**を右クリックし、 **SimpleProject**プロジェクト ノードをポイントして、**追加**、 をクリックし、**新しいフォルダー**します。 フォルダーの名前*テンプレート*します。 *テンプレート*フォルダー、という名前のフォルダーを追加*プロジェクト*します。 *プロジェクト*フォルダー、という名前のフォルダーを追加*SimpleProject*)。  
  
2.  *Templates\Projects\SimpleProject*フォルダー、という名前のアイコンとして使用するビットマップ イメージ ファイルを追加*SimpleProject.ico*します。 クリックすると**追加**、アイコン エディターが開きます。  
  
3.  特徴的なアイコンを確認します。 このアイコンが表示、**新しいプロジェクト**チュートリアルの後半でダイアログ ボックス。  
  
     ![単純なプロジェクト アイコン](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  アイコンを保存してアイコン エディターを閉じます。  
  
5.  *Templates\Projects\SimpleProject*フォルダーを追加、**クラス**という名前の項目*Program.cs*します。  
  
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
    >  これはの最終形式ではありません、 *Program.cs*コード、パラメーターの処理後の手順で置換します。 表示されるコンパイル エラーしますが、いる限り、ファイルの **"ビルド アクション"** は**コンテンツ**をビルドして、プロジェクトを通常どおり実行できる必要があります。  
  
1.  ファイルを保存します。  
  
2.  コピー、 *AssemblyInfo.cs*ファイルから、*プロパティ*フォルダーを*Projects\SimpleProject*フォルダー。  
  
3.  *Projects\SimpleProject*フォルダーという XML ファイルを追加する*SimpleProject.myproj*します。  
  
    > [!NOTE]
    >  この種類のすべてのプロジェクトのファイル名拡張子は *.myproj*します。 これを変更する場合をチュートリアルで説明したようにすべての場所に変更する必要があります。  
  
4.  既存のコンテンツを次の行に置き換えます。  
  
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
  
6.  **プロパティ**ウィンドウで、設定、**ビルド アクション**の*AssemblyInfo.cs*、 *Program.cs*、 *SimpleProject.ico*と*SimpleProject.myproj*に**コンテンツ**、設定とその**VSIX に含める**プロパティを**True**.  
  
 このプロジェクト テンプレートには、基本的な Visual c# プロジェクトをデバッグ構成とリリース構成の両方を持つがについて説明します。 プロジェクトには、2 つのソース ファイルが含まれています。 *AssemblyInfo.cs*と*Program.cs*、およびいくつかのアセンブリ参照。 テンプレートからプロジェクトが作成されると、ProjectGuid 値が自動的に新しい GUID によって置き換えられます。  
  
 **ソリューション エクスプ ローラー**、展開された**テンプレート**フォルダーが次のように表示されます。

```
Templates  
   Projects  
      SimpleProject  
         AssemblyInfo.cs  
         Program.cs  
         SimpleProject.ico  
         SimpleProject.myproj  
```

## <a name="create-a-basic-project-factory"></a>基本的なプロジェクト ファクトリを作成します。  
 Visual Studio プロジェクト テンプレート フォルダーの場所に指示する必要があります。 これを行うには、テンプレートの場所は、VSPackage をビルドするときに、システム レジストリに書き込まれるようにプロジェクト ファクトリを実装する VSPackage クラスに属性を追加します。 まずプロジェクト ファクトリ GUID によって識別される基本的なプロジェクト ファクトリを作成します。 使用して、<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>をプロジェクト ファクトリを接続属性、`SimpleProjectPackage`クラス。  
  
### <a name="to-create-a-basic-project-factory"></a>基本的なプロジェクト ファクトリを作成するには  
  
1.  プロジェクト ファクトリの Guid を作成する (上、**ツール** メニューのをクリックして**GUID の作成**)、か、次の例を使用します。 追加する Guid、`SimpleProjectPackage`セクションには、既に定義されているお近くのクラス`PackageGuidString`します。 Guid は、GUID 形式と文字列形式の両方である必要があります。 結果として得られるコードは次の例のようになります。  
  
    ```csharp  
        public sealed class SimpleProjectPackage : Package
        {  
            ...
            public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
            public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
    
            public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);  
        }  
    ```  
  
3.  クラスを追加、ページのトップへ*SimpleProject*という名前のフォルダー *SimpleProjectFactory.cs*します。  
  
4.  次の追加ステートメントを使用します。  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  GUID 属性を追加、`SimpleProjectFactory`クラス。 属性の値は、新しいプロジェクト ファクトリの GUID です。  
  
    ```csharp  
    [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 これで、プロジェクト テンプレートを登録できます。  
  
### <a name="to-register-the-project-template"></a>プロジェクト テンプレートを登録するには  
  
1.  *SimpleProjectPackage.cs*、追加、<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>属性を`SimpleProjectPackage`クラスに、次のようにします。  
  
    ```csharp  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectPackage.PackageGuidString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  ソリューションをリビルドし、エラーなしでビルドされることを確認します。  
  
     再構築するには、プロジェクト テンプレートが登録します。  
  
 パラメーター`defaultProjectExtension`と`possibleProjectExtensions`プロジェクトのファイル名拡張子に設定されます (*.myproj*)。 `projectTemplatesDirectory`パラメーターの相対パスに設定されて、*テンプレート*フォルダー。 ビルド中には、このパスをフル ビルドに変換され、プロジェクト システムに登録するレジストリに追加するされます。  
  
## <a name="test-the-template-registration"></a>テンプレート登録をテストします。  
 テンプレート登録は Visual Studio プロジェクト テンプレート フォルダーの場所 Visual Studio は、テンプレートの名前とアイコンを表示できるように、**新しいプロジェクト** ダイアログ ボックス。  
  
### <a name="to-test-the-template-registration"></a>テンプレート登録をテストするには  
  
1.  キーを押して**F5** Visual Studio の実験用インスタンスのデバッグを開始します。  
  
2.  実験用インスタンスで、新しく作成されたプロジェクトの種類の新しいプロジェクトを作成します。 **新しいプロジェクト**] ダイアログ ボックスに、表示する必要があります**SimpleProject** [**にインストールされたテンプレート**します。  
  
 登録されているプロジェクト ファクトリがあるようになりました。 ただし、プロジェクトをまだ作成できません。 プロジェクトのパッケージとプロジェクト ファクトリを作成し、プロジェクトの初期化に連携します。  
  
## <a name="add-the-managed-package-framework-code"></a>Managed Package Framework のコードを追加します。  
 プロジェクト パッケージとプロジェクト ファクトリ間の接続を実装します。  
  
-   Managed Package Framework のソース コード ファイルをインポートします。  
  
    1.  SimpleProject プロジェクトのアンロード (で**ソリューション エクスプ ローラー**プロジェクト ノードを選択し、コンテキスト メニューで、**プロジェクトのアンロード**。) XML エディターでプロジェクト ファイルを開きます。  
  
    2.  プロジェクト ファイルに、次の要素を追加 (すぐ上、\<インポート > ブロック)。 設定`ProjectBasePath`の場所に、 *ProjectBase.files* Managed Package Framework コードをダウンロードしたファイル。 パス名に円記号を追加する必要があります。 そうでない Managed Package Framework のソース コードを検索するプロジェクトが失敗する可能性があります。  
  
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
  
        -   `Microsoft.VisualStudio.Designer.Interfaces` (で *\<VSSDK インストール > \VisualStudioIntegration\Common\Assemblies\v2.0*)  
  
        -   `WindowsBase`  
  
        -   `Microsoft.Build.Tasks.v4.0`  
  
### <a name="to-initialize-the-project-factory"></a>プロジェクト ファクトリを初期化するには  
  
1.  *SimpleProjectPackage.cs*ファイルで、次の追加`using`ステートメント。  
  
    ```csharp  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  派生、`SimpleProjectPackage`クラス`Microsoft.VisualStudio.Package.ProjectPackage`します。  
  
    ```csharp  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  プロジェクト ファクトリを登録します。 次の行を追加、`SimpleProjectPackage.Initialize`メソッド直後`base.Initialize`します。  
  
    ```csharp  
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
  
5.  *SimpleProjectFactory.cs*、次の追加`using`後、既存のステートメント`using`ステートメント。  
  
    ```csharp  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  派生、`SimpleProjectFactory`クラス`ProjectFactory`します。  
  
    ```csharp  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  次のダミー メソッドを追加、`SimpleProjectFactory`クラス。 後のセクションでは、このメソッドを実装します。  
  
    ```csharp  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  次のフィールドとコンス トラクターを追加、`SimpleProjectFactory`クラス。 これは、`SimpleProjectPackage`参照が、プライベート フィールドにキャッシュされるので、サービス プロバイダーのサイトの設定で使用できます。  
  
    ```csharp  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. ソリューションをリビルドし、エラーなしでビルドされることを確認します。  
  
## <a name="test-the-project-factory-implementation"></a>プロジェクト ファクトリの実装をテストします。  
 プロジェクト ファクトリの実装のコンス トラクターを呼び出すかどうかをテストします。  
  
### <a name="to-test-the-project-factory-implementation"></a>プロジェクト ファクトリの実装をテストするには  
  
1.  *SimpleProjectFactory.cs*ファイルで、次の行にブレークポイントを設定、`SimpleProjectFactory`コンス トラクター。  
  
    ```csharp  
    this.package = package;  
    ```  
  
2.  キーを押して**F5**を Visual Studio の実験用インスタンスを開始します。  
  
3.  実験用インスタンスでは、新しいプロジェクトを作成を開始します。 **新しいプロジェクト**ダイアログ ボックスで、 **SimpleProject**プロジェクトの種類をクリックして**OK**します。 ブレークポイントで実行が停止します。  
  
4.  ブレークポイントを解除し、デバッグを停止します。 まだ作成していないプロジェクト ノードため、プロジェクトの作成コードが例外をスローします。  
  
## <a name="extend-the-projectnode-class"></a>ProjectNode クラスを拡張します。  
 実装することができますので、`SimpleProjectNode`から派生したクラス、`ProjectNode`クラス。 `ProjectNode`基底クラスは、プロジェクトの作成の次のタスクを処理します。  
  
-   プロジェクト テンプレート ファイルのコピー *SimpleProject.myproj*、新しいプロジェクト フォルダーにします。 入力された名前に基づいてコピーの名前が変更された、**新しいプロジェクト** ダイアログ ボックス。 `ProjectGuid`プロパティの値は、新しい GUID によって置き換えられます。  
  
-   プロジェクト テンプレート ファイルの MSBuild 要素を走査*SimpleProject.myproj*、検索と`Compile`要素。 各`Compile`ターゲット ファイルでは、新しいプロジェクト フォルダーにファイルをコピーします。  
  
 派生した`SimpleProjectNode`クラスは、これらのタスクを処理します。  
  
-   内のプロジェクトとファイルのノードのアイコンにより、**ソリューション エクスプ ローラー**作成または選択します。  
  
-   指定するその他のプロジェクト テンプレートのパラメーター置換を有効にします。  
  
### <a name="to-extend-the-projectnode-class"></a>ProjectNode クラスを拡張するには  
  
1.  という名前のクラスを追加`SimpleProjectNode.cs`します。  
  
2.  既存のコードを次のコードに置き換えます。  
  
    ```csharp  
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
                get { return SimpleProjectPackage.guidSimpleProjectFactory; }  
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
  
-   `AddFileFromTemplate`、対象のプロジェクトにテンプレート フォルダーから選択したファイルをコピーします。 このメソッドは、後のセクションでさらに実装されます。  
  
 `SimpleProjectNode`コンス トラクターと同様に、`SimpleProjectFactory`コンス トラクターは、キャッシュ、`SimpleProjectPackage`後で使用できるプライベート フィールドで参照します。  
  
 接続する、`SimpleProjectFactory`クラスを`SimpleProjectNode`クラスをインスタンス化して、新しい`SimpleProjectNode`で、`SimpleProjectFactory.CreateProject`メソッドと後で使用できるプライベート フィールドにキャッシュします。  
  
### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>プロジェクトのファクトリ クラスと、ノード クラスに接続するには  
  
1.  *SimpleProjectFactory.cs*ファイルで、次の追加`using`ステートメント。  
  
    ```csharp  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  置換、`SimpleProjectFactory.CreateProject`メソッドを次のコードを使用します。  
  
    ```csharp  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  ソリューションをリビルドし、エラーなしでビルドされることを確認します。  
  
## <a name="test-the-projectnode-class"></a>ProjectNode クラスをテストします。  
 プロジェクト階層を作成するかどうかを確認する、プロジェクト ファクトリをテストします。  
  
### <a name="to-test-the-projectnode-class"></a>ProjectNode クラスをテストするには  
  
1.  **F5** キーを押してデバッグを開始します。 実験用のインスタンスでは、新しい SimpleProject を作成します。  
  
2.  Visual Studio では、プロジェクトを作成する、プロジェクト ファクトリを呼び出す必要があります。  
  
3.  Visual Studio の実験用インスタンスを終了します。  
  
## <a name="add-a-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンを追加します。  
 前のセクションでは、プロジェクト ノードのアイコンは、既定のアイコンです。 カスタム アイコンに変更することができます。  
  
### <a name="to-add-a-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンを追加するには  
  
1.  **リソース**フォルダー、という名前のビットマップ ファイルを追加*SimpleProjectNode.bmp*します。  
  
2.  **プロパティ**windows では 16 x 16 ピクセルにビットマップを削減します。 特徴的なビットマップを作成します。  
  
     ![単純なプロジェクト Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  **プロパティ**ウィンドウで、変更、**ビルド アクション**するビットマップの**埋め込まれたリソース**します。  
  
4.  *SimpleProjectNode.cs*、次の追加`using`ステートメント。  
  
    ```csharp  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  次の静的フィールドとコンス トラクターを追加、`SimpleProjectNode`クラス。  
  
    ```csharp  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  先頭に次のプロパティを追加、`SimpleProjectNode`クラス。  
  
    ```csharp  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  インスタンス コンス トラクターを次のコードに置き換えます。  
  
    ```csharp  
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
  
 静的の構築時に`SimpleProjectNode`アセンブリのマニフェスト リソースから、プロジェクト ノードのビットマップを取得し、後で使用できるプライベート フィールドにそれをキャッシュします。 構文に注意してください、<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>イメージのパス。 アセンブリに埋め込まれたマニフェスト リソースの名前を表示するには、使用、<xref:System.Reflection.Assembly.GetManifestResourceNames%2A>メソッド。 このメソッドを適用すると、`SimpleProject`アセンブリ、結果は、次のようにする必要があります。  
  
-   *SimpleProject.Resources.resources*  
  
-   *VisualStudio.Project.resources*  
  
-   *SimpleProject.VSPackage.resources*  
  
-   *Resources.imagelis.bmp*  
  
-   *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*  
  
-   *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*  
  
-   *SimpleProject.Resources.SimpleProjectNode.bmp*  
  
 インスタンスの構築時に、`ProjectNode`クラスの読み込みの基本*Resources.imagelis.bmp*から 16 x 16 ビットマップを使用してよくが埋め込まれている*Resources\imagelis.bmp*します。 このビットマップの一覧が利用可能になります`SimpleProjectNode`として`ImageHandler.ImageList`します。 `SimpleProjectNode` 一覧には、プロジェクト ノードのビットマップを追加します。 イメージ リストでプロジェクト ノードのビットマップのオフセットは、パブリックの値として後で使用できるキャッシュ`ImageIndex`プロパティ。 Visual Studio では、このプロパティを使用して、プロジェクト ノードのアイコンとして表示するには、どのビットマップを調べます。  
  
## <a name="test-the-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンをテストします。  
 カスタムのプロジェクト ノードのアイコンを含むプロジェクト階層を作成するかどうかを確認する、プロジェクト ファクトリをテストします。  
  
### <a name="to-test-the-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンをテストするには  
  
1.  デバッグを開始し、実験用インスタンスで新しい SimpleProject を作成します。  
  
2.  新しく作成されたプロジェクトで*SimpleProjectNode.bmp*プロジェクト ノードのアイコンとして使用されます。  
  
     ![新しいプロジェクト ノードを単純なプロジェクト](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  開いている*Program.cs*コード エディターにします。 次のコードのようなソース コードが表示されます。  
  
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
  
     $NameSpace$ と $className$ のテンプレート パラメーターに新しい値がないことに注意してください。 次のセクションで、テンプレート パラメーターの置換を実装する方法を学習します。  
  
## <a name="substitute-template-parameters"></a>テンプレートのパラメーターを置き換える  
 前のセクションで登録したプロジェクト テンプレートで Visual Studio を使用して、`ProvideProjectFactory`属性。 テンプレート フォルダーのパスをこの方法で登録をオーバーライドし、展開する基本的なテンプレート パラメーターの置換を有効にすることができます、`ProjectNode.AddFileFromTemplate`クラス。 詳細については、次を参照してください。[新しいプロジェクトの生成: 内部、パート 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)します。  
  
 交換用のコードを追加、`AddFileFromTemplate`クラス。  
  
### <a name="to-substitute-template-parameters"></a>テンプレート パラメーター値  
  
1.  *SimpleProjectNode.cs*ファイルで、次の追加`using`ステートメント。  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  置換、`AddFileFromTemplate`メソッドを次のコードを使用します。  
  
    ```csharp  
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
  
 代入ステートメントは、名前空間と新しいクラス名の妥当な値を決定します。 2 つ`ProjectNode.FileTemplateProcessor.AddReplace`メソッドの呼び出しは、これらの新しい値を使用して、対応するテンプレート パラメーターの値を置き換えます。  
  
## <a name="test-the-template-parameter-substitution"></a>テンプレート パラメーターの置換をテストします。  
 テンプレート パラメーターの置換をテストできます。  
  
### <a name="to-test-the-template-parameter-substitution"></a>テンプレート パラメーターの置換をテストするには  
  
1.  デバッグを開始し、実験用インスタンスで新しい SimpleProject を作成します。  
  
2.  内のブレークポイントで実行が停止、`AddFileFromTemplate`メソッド。  
  
3.  値を調べ、`nameSpace`と`className`パラメーター。  
  
    -   `nameSpace` 値が指定されて、 \<RootNamespace > 内の要素、 *\Templates\Projects\SimpleProject\SimpleProject.myproj*プロジェクト テンプレート ファイル。 この場合、値は `MyRootNamespace` です。  
  
    -   `className` ファイル名拡張子を除いた、クラスのソース ファイル名の値が指定されています。 最初のファイル変換先のフォルダーにコピーするのには、この場合、 *AssemblyInfo.cs*。 したがって、クラス名の値が`AssemblyInfo`します。  
  
4.  ブレークポイントとキーを押して削除**F5**の実行を続行します。  
  
     Visual Studio では、プロジェクトの作成を完了する必要があります。  
  
5.  開いている*Program.cs*コード エディターにします。 次のコードのようなソース コードが表示されます。  
  
    ```csharp  
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
  
     名前空間は、今すぐ通知`MyRootNamespace`クラス名が、現在は`Program`します。  
  
6.  プロジェクトのデバッグを開始します。 新しいプロジェクトがコンパイル、実行、および「VSX こんにちは!!!」と表示 コンソール ウィンドウに表示します。  
  
     ![単純なプロジェクト コマンド](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 おめでとうございます! マネージ プロジェクトは、基本的なシステムを実装しました。