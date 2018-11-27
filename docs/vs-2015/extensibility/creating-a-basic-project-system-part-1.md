---
title: 基本的なプロジェクト システムを作成するには、パート 1 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9bc0be22f0a5f975f616bfcce942d59399a36ad6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792555"
---
# <a name="creating-a-basic-project-system-part-1"></a>基本的なプロジェクト システムの作成、パート 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio では、プロジェクトは、開発者は、ソース コード ファイルおよびその他の資産の分類に使用するコンテナーです。 プロジェクトがソリューション内の子として表示されます、**ソリューション エクスプ ローラー**します。 プロジェクトでは、整理、ビルド、デバッグ、およびソース コードをデプロイおよび Web サービス、データベース、およびその他のリソースへの参照を作成できます。  
  
 プロジェクトは、たとえば Visual c# プロジェクトの .csproj ファイルをプロジェクト ファイルで定義されます。 独自のプロジェクト ファイル名拡張子を持つ独自のプロジェクトの種類を作成することができます。 プロジェクトの種類の詳細については、次を参照してください。[プロジェクトの種類](../extensibility/internals/project-types.md)します。  
  
> [!NOTE]
>  カスタムのプロジェクトの種類の Visual Studio を拡張する必要がある場合強くお勧めしますを活用すること、 [Visual Studio プロジェクト システム](https://github.com/Microsoft/VSProjectSystem)はさまざまなプロジェクト システムを一から構築に比べて利点があります。  
> 
> - 簡単にオンボードします。  基本的なプロジェクト システムではさらには、数万行のコードの必要があります。  前に、お客様のニーズに合わせてカスタマイズする準備が整ったら、ほんの数回のクリックにオンボード コストを削減する CPS を活用すること。  
>   -   メンテナンスを容易にします。  CPS を活用することによってのみ、独自のシナリオを維持する必要があります。  すべてのプロジェクト システム インフラストラクチャの保守管理を処理します。  
> 
>   Visual Studio の Visual Studio 2013 より前のバージョンをターゲットする必要がある場合、Visual Studio 拡張機能で CPS を活用することができなきます。  場合は、このチュートリアルでは開始することをお勧めします。  
  
 このチュートリアルでは、プロジェクト ファイル名拡張子 .myproj を含むプロジェクトの種類を作成する方法を示します。 このチュートリアルでは既存の Visual c# プロジェクト システムを利用します。  
  
> [!NOTE]
>  エンド ツー エンドのサンプルの完全な言語のプロジェクト システムで IronPython サンプルの詳細情報を参照してください。 [VSSDK のサンプル](../misc/vssdk-samples.md)します。  
  
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
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
 ソース コードをダウンロードすることも必要があります、[プロジェクト用 Managed Package Framework](http://mpfproj12.codeplex.com/)します。 作成しようとするソリューションにアクセスできる場所にファイルを抽出します。  
  
## <a name="creating-a-basic-project-type"></a>基本的なプロジェクトの種類を作成します。  
 という名前の c# VSIX プロジェクトを作成する**SimpleProject**します。 (**新しいファイル]、[プロジェクト**し**c#、機能拡張、Visual Studio パッケージ**)。 Visual Studio パッケージ プロジェクト項目テンプレートを追加する (ソリューション エクスプ ローラーでプロジェクト ノードを右クリックし、選択**追加/新しい項目の**に移動し、**拡張機能/Visual Studio パッケージ**)。 ファイルに名前を**SimpleProjectPackage**します。  
  
## <a name="creating-a-basic-project-template"></a>基本的なプロジェクト テンプレートを作成します。  
 ここで、新しい .myproj プロジェクトの種類を実装するためにこの基本的な VSPackage を変更できます。 .Myproj プロジェクトの種類に基づくプロジェクトを作成するには、Visual Studio をどのファイル、リソース、および新しいプロジェクトに追加する参照を知る必要があります。 この情報を提供するには、プロジェクトのテンプレート フォルダーにプロジェクト ファイルを配置します。 ユーザーは、プロジェクトを作成する .myproj プロジェクトを使用するときに、ファイルは、新しいプロジェクトにコピーされます。  
  
#### <a name="to-create-a-basic-project-template"></a>基本的なプロジェクト テンプレートを作成するには  
  
1. 3 つのフォルダーを他のいずれかと、プロジェクトに追加: **Templates\Projects\SimpleProject**します。 (で**ソリューション エクスプ ローラー**を右クリックし、 **SimpleProject**プロジェクト ノードをポイントして、**追加**、 をクリックし、**新しいフォルダー**します。 フォルダーに「 `Templates`で行うことができます。 **テンプレート**フォルダー、という名前のフォルダーを追加`Projects`します。 **プロジェクト**フォルダー、という名前のフォルダーを追加`SimpleProject`)。  
  
2. **Projects\SimpleProject**という名前のアイコン ファイルをフォルダーに追加`SimpleProject.ico`します。 クリックすると**追加**、アイコン エディターが開きます。  
  
3. 特徴的なアイコンを確認します。 このアイコンが表示、**新しいプロジェクト**チュートリアルの後半でダイアログ ボックス。  
  
    ![単純なプロジェクト アイコン](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4. アイコンを保存してアイコン エディターを閉じます。  
  
5. **Projects\SimpleProject**フォルダーを追加、**クラス**という名前の項目`Program.cs`します。  
  
6. 既存のコードを次の行に置き換えます。  
  
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
   >  これは、Program.cs のコードの最終形式ではありません。置換パラメーターの後の手順で処理します。 表示されるコンパイル エラーしますが、いる限り、ファイルの **"ビルド アクション"** は**コンテンツ**をビルドして、プロジェクトを通常どおり実行できる必要があります。  
  
7. ファイルを保存します。  
  
8. AssemblyInfo.cs ファイルのコピー、**プロパティ**フォルダーを**Projects\SimpleProject**フォルダー。  
  
9. **Projects\SimpleProject**フォルダーという XML ファイルを追加する`SimpleProject.myproj`します。  
  
   > [!NOTE]
   >  この種類のすべてのプロジェクトのファイル名拡張子は、.myproj です。 これを変更する場合をチュートリアルで説明したようにすべての場所に変更する必要があります。  
  
10. 既存のコンテンツを次の行に置き換えます。  
  
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
  
11. ファイルを保存します。  
  
12. **プロパティ**ウィンドウで、設定、**ビルド アクション**AssemblyInfo.cs、Program.cs、SimpleProject.ico、およびに SimpleProject.myproj の**コンテンツ**、し、そのの設定**VSIX に含める**プロパティ**True**します。  
  
    このプロジェクト テンプレートには、基本的な Visual c# プロジェクトをデバッグ構成とリリース構成の両方を持つがについて説明します。 プロジェクトには、2 つのソース ファイル、AssemblyInfo.cs、Program.cs、およびいくつかのアセンブリが含まれています。 参照。 テンプレートからプロジェクトが作成されると、ProjectGuid 値が自動的に新しい GUID によって置き換えられます。  
  
    **ソリューション エクスプ ローラー**、展開された**テンプレート**フォルダーが次のように表示されます。  
  
    テンプレート  
  
    プロジェクト  
  
    SimpleProject  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    SimpleProject.ico  
  
    SimpleProject.myproj  
  
## <a name="creating-a-basic-project-factory"></a>基本的なプロジェクト ファクトリを作成します。  
 Visual Studio プロジェクト テンプレート フォルダーの場所に指示する必要があります。 これを行うには、テンプレートの場所は、VSPackage をビルドするときに、システム レジストリに書き込まれるようにプロジェクト ファクトリを実装する VSPackage クラスに属性を追加します。 まずプロジェクト ファクトリ GUID によって識別される基本的なプロジェクト ファクトリを作成します。 使用して、 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> SimpleProjectPackage クラスをプロジェクト ファクトリを接続する属性。  
  
#### <a name="to-create-a-basic-project-factory"></a>基本的なプロジェクト ファクトリを作成するには  
  
1. SimpleProjectPackageGuids.cs をコード エディターで開きます。  
  
2. プロジェクト ファクトリの Guid を作成する (上、**ツール** メニューのをクリックして**GUID の作成**)、か、次の例を使用します。 Guid を SimpleProjectPackageGuids クラスに追加します。 Guid は、GUID 形式と文字列形式の両方である必要があります。 結果として得られるコードは次の例のようになります。  
  
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
  
3. クラスを追加、ページのトップへ**SimpleProject**という名前のフォルダー`SimpleProjectFactory.cs`します。  
  
4. 次の追加ステートメントを使用します。  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. Guid 属性を SimpleProjectFactory クラスに追加します。 属性の値は、新しいプロジェクト ファクトリの GUID です。  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   これで、プロジェクト テンプレートを登録できます。  
  
#### <a name="to-register-the-project-template"></a>プロジェクト テンプレートを登録するには  
  
1. SimpleProjectPackage.cs で追加、<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>属性、SimpleProjectPackage クラスを次のようにします。  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. ソリューションをリビルドし、エラーなしでビルドされることを確認します。  
  
    再構築するには、プロジェクト テンプレートが登録します。  
  
   パラメーター`defaultProjectExtension`と`possibleProjectExtensions`プロジェクト ファイル名拡張子 (.myproj) に設定されます。 `projectTemplatesDirectory`パラメーター テンプレート フォルダーの相対パスに設定されます。 ビルド中には、このパスをフル ビルドに変換され、プロジェクト システムに登録するレジストリに追加するされます。  
  
## <a name="testing-the-template-registration"></a>テンプレート登録をテストします。  
 テンプレート登録は Visual Studio プロジェクト テンプレート フォルダーの場所 Visual Studio は、テンプレートの名前とアイコンを表示できるように、**新しいプロジェクト** ダイアログ ボックス。  
  
#### <a name="to-test-the-template-registration"></a>テンプレート登録をテストするには  
  
1. F5 キーを押して、Visual Studio の実験用インスタンスのデバッグを開始します。  
  
2. 実験用インスタンスで、新しく作成されたプロジェクトの種類の新しいプロジェクトを作成します。 **新しいプロジェクト**] ダイアログ ボックスに、表示する必要があります**SimpleProject** [**にインストールされたテンプレート**します。  
  
   登録されているプロジェクト ファクトリがあるようになりました。 ただし、プロジェクトをまだ作成できません。 プロジェクトのパッケージとプロジェクト ファクトリを作成し、プロジェクトの初期化に連携します。  
  
## <a name="add-the-managed-package-framework-code"></a>Managed Package Framework のコードを追加します。  
 プロジェクト パッケージとプロジェクト ファクトリ間の接続を実装します。  
  
-   Managed Package Framework のソース コード ファイルをインポートします。  
  
    1.  SimpleProject プロジェクトのアンロード (で**ソリューション エクスプ ローラー**プロジェクト ノードを選択し、コンテキスト メニューで、**プロジェクトのアンロード**。) XML エディターでプロジェクト ファイルを開きます。  
  
    2.  プロジェクト ファイルに、次の要素を追加 (すぐ上、\<インポート > ブロック)。 ProjectBasePath をダウンロードした Managed Package Framework コードで ProjectBase.files ファイルの場所に設定します。 パス名に円記号を追加する必要があります。 そうでない Managed Package Framework のコードを検索するプロジェクトが失敗する可能性があります。  
  
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
  
#### <a name="to-initialize-the-project-factory"></a>プロジェクト ファクトリを初期化するには  
  
1.  SimpleProjectPackage.cs ファイルで次の追加`using`ステートメント。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  派生、`SimpleProjectPackage`クラス`Microsoft.VisualStudio.Package.ProjectPackage`します。  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  プロジェクト ファクトリを登録します。 次の行を追加、`SimpleProjectPackage.Initialize`メソッド直後`base.Initialize`します。  
  
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
  
5.  SimpleProjectFactory.cs で、次のコードを追加`using`後、既存のステートメント`using`ステートメント。  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  派生、`SimpleProjectFactory`クラス`ProjectFactory`します。  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  次のダミー メソッドを追加、`SimpleProjectFactory`クラス。 後のセクションでは、このメソッドを実装します。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  次のフィールドとコンス トラクターを追加、`SimpleProjectFactory`クラス。 これは、`SimpleProjectPackage`参照が、プライベート フィールドにキャッシュされるので、サービス プロバイダーのサイトの設定で使用できます。  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. ソリューションをリビルドし、エラーなしでビルドされることを確認します。  
  
## <a name="testing-the-project-factory-implementation"></a>プロジェクト ファクトリの実装をテストします。  
 プロジェクト ファクトリの実装のコンス トラクターを呼び出すかどうかをテストします。  
  
#### <a name="to-test-the-project-factory-implementation"></a>プロジェクト ファクトリの実装をテストするには  
  
1.  SimpleProjectFactory.cs ファイルでは、次の行にブレークポイントを設定、`SimpleProjectFactory`コンス トラクター。  
  
    ```  
    this.package = package;  
    ```  
  
2.  F5 キーを押して、Visual Studio の実験用インスタンスを起動します。  
  
3.  実験用インスタンスでは、新しいプロジェクトを作成を開始します。**新しいプロジェクト**ダイアログ ボックスで、SimpleProject プロジェクトの種類をクリックして**OK**します。 ブレークポイントで実行が停止します。  
  
4.  ブレークポイントを解除し、デバッグを停止します。 まだ作成していないプロジェクト ノードため、プロジェクトの作成コードが例外をスローします。  
  
## <a name="extending-the-project-node-class"></a>プロジェクト ノードのクラスを拡張します。  
 実装することができますので、`SimpleProjectNode`から派生したクラス、`ProjectNode`クラス。 `ProjectNode`基底クラスは、プロジェクトの作成の次のタスクを処理します。  
  
- プロジェクトのテンプレート ファイル、SimpleProject.myproj を新しいプロジェクト フォルダーにコピーします。 入力された名前に基づいてコピーの名前が変更された、**新しいプロジェクト** ダイアログ ボックス。 `ProjectGuid`プロパティの値は、新しい GUID によって置き換えられます。  
  
- プロジェクトのテンプレート ファイル、SimpleProject.myproj の MSBuild 要素を走査し、検索`Compile`要素。 各`Compile`ターゲット ファイルでは、新しいプロジェクト フォルダーにファイルをコピーします。  
  
  派生した`SimpleProjectNode`クラスは、これらのタスクを処理します。  
  
- 内のプロジェクトとファイルのノードのアイコンにより、**ソリューション エクスプ ローラー**作成または選択します。  
  
- 指定するその他のプロジェクト テンプレートのパラメーター置換を有効にします。  
  
#### <a name="to-extend-the-project-node-class"></a>プロジェクト ノードのクラスを拡張するには  
  
1. 
  
2. という名前のクラスを追加`SimpleProjectNode.cs`します。  
  
3. 既存のコードを次のコードに置き換えます。  
  
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
  
- `ProjectGuid`をプロジェクト ファクトリ GUID が返されます。  
  
- `ProjectType`、プロジェクトの種類のローカライズされた名前が返されます。  
  
- `AddFileFromTemplate`、対象のプロジェクトにテンプレート フォルダーから選択したファイルをコピーします。 このメソッドは、後のセクションでさらに実装されます。  
  
  `SimpleProjectNode`コンス トラクターと同様に、`SimpleProjectFactory`コンス トラクターは、キャッシュ、`SimpleProjectPackage`後で使用できるプライベート フィールドで参照します。  
  
  接続する、`SimpleProjectFactory`クラスを`SimpleProjectNode`クラスをインスタンス化して、新しい`SimpleProjectNode`で、`SimpleProjectFactory.CreateProject`メソッドと後で使用できるプライベート フィールドにキャッシュします。  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>プロジェクトのファクトリ クラスと、ノード クラスに接続するには  
  
1.  SimpleProjectFactory.cs ファイルで次の追加`using`ステートメント。  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  置換、`SimpleProjectFactory.CreateProject`メソッドを次のコードを使用します。  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  ソリューションをリビルドし、エラーなしでビルドされることを確認します。  
  
## <a name="testing-the-project-node-class"></a>プロジェクト ノードのクラスのテスト  
 プロジェクト階層を作成するかどうかを確認する、プロジェクト ファクトリをテストします。  
  
#### <a name="to-test-the-project-node-class"></a>プロジェクト ノードのクラスをテストするには  
  
1.  F5 キーを押してデバッグを開始します。 実験用のインスタンスでは、新しい SimpleProject を作成します。  
  
2.  Visual Studio では、プロジェクトを作成する、プロジェクト ファクトリを呼び出す必要があります。  
  
3.  Visual Studio の実験用インスタンスを終了します。  
  
## <a name="adding-a-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンの追加  
 前のセクションでは、プロジェクト ノードのアイコンは、既定のアイコンです。 カスタム アイコンに変更することができます。  
  
#### <a name="to-add-a-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンを追加するには  
  
1. **リソース**フォルダー、SimpleProjectNode.bmp をという名前のビットマップ ファイルを追加します。  
  
2. **プロパティ**windows では 16 x 16 ピクセルにビットマップを削減します。 特徴的なビットマップを作成します。  
  
    ![単純なプロジェクト Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3. **プロパティ**ウィンドウで、変更、**ビルド アクション**するビットマップの**埋め込まれたリソース**します。  
  
4. SimpleProjectNode.cs で、次のコードを追加`using`ステートメント。  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. 次の静的フィールドとコンス トラクターを追加、`SimpleProjectNode`クラス。  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. 先頭に次のプロパティを追加、`SimpleProjectNode`クラス。  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. インスタンス コンス トラクターを次のコードに置き換えます。  
  
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
  
   静的の構築時に`SimpleProjectNode`アセンブリのマニフェスト リソースから、プロジェクト ノードのビットマップを取得し、後で使用できるプライベート フィールドにそれをキャッシュします。 構文に注意してください、<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>イメージのパス。 アセンブリに埋め込まれたマニフェスト リソースの名前を表示するには、使用、<xref:System.Reflection.Assembly.GetManifestResourceNames%2A>メソッド。 このメソッドを適用すると、`SimpleProject`アセンブリ、結果は、次のようにする必要があります。  
  
- SimpleProject.Resources.resources  
  
- VisualStudio.Project.resources  
  
- SimpleProject.VSPackage.resources  
  
- Resources.imagelis.bmp  
  
- Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
- Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
- SimpleProject.Resources.SimpleProjectNode.bmp  
  
  インスタンスの構築時に、`ProjectNode`基底クラスの Resources\imagelis.bmp から一般的に使用される埋め込みの 16 x 16 ビットマップ Resources.imagelis.bmp を読み込みます。 このビットマップの一覧が利用可能になります`SimpleProjectNode`ImageHandler.ImageList として。 `SimpleProjectNode` 一覧には、プロジェクト ノードのビットマップを追加します。 イメージ リストでプロジェクト ノードのビットマップのオフセットは、パブリックの値として後で使用できるキャッシュ`ImageIndex`プロパティ。 Visual Studio では、このプロパティを使用して、プロジェクト ノードのアイコンとして表示するには、どのビットマップを調べます。  
  
## <a name="testing-the-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンのテスト  
 カスタムのプロジェクト ノードのアイコンを含むプロジェクト階層を作成するかどうかを確認する、プロジェクト ファクトリをテストします。  
  
#### <a name="to-test-the-custom-project-node-icon"></a>カスタム プロジェクト ノードのアイコンをテストするには  
  
1.  デバッグを開始し、実験用インスタンスで新しい SimpleProject を作成します。  
  
2.  新しく作成されたプロジェクトで SimpleProjectNode.bmp がプロジェクト ノードのアイコンとして使用されることに注意してください。  
  
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
  
     $NameSpace$ と $className$ のテンプレート パラメーターに新しい値がないことに注意してください。 次のセクションで、テンプレート パラメーターの置換を実装する方法を学習します。  
  
## <a name="substituting-template-parameters"></a>テンプレート パラメーターの置換  
 前のセクションで登録したプロジェクト テンプレートで Visual Studio を使用して、`ProvideProjectFactory`属性。 テンプレート フォルダーのパスをこの方法で登録をオーバーライドし、展開する基本的なテンプレート パラメーターの置換を有効にすることができます、`ProjectNode.AddFileFromTemplate`クラス。 詳細については、次を参照してください。[新しいプロジェクトの生成: 内部、パート 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)します。  
  
 交換用のコードを追加、`AddFileFromTemplate`クラス。  
  
#### <a name="to-substitute-template-parameters"></a>テンプレート パラメーター値  
  
1. SimpleProjectNode.cs ファイルで次の追加`using`ステートメント。  
  
   ```  
   using System.IO;  
   ```  
  
2. 置換、`AddFileFromTemplate`メソッドを次のコードを使用します。  
  
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
  
3. 直後に、メソッドにブレークポイントを設定、`className`代入ステートメント。  
  
   代入ステートメントは、名前空間と新しいクラス名の妥当な値を決定します。 2 つ`ProjectNode.FileTemplateProcessor.AddReplace`メソッドの呼び出しは、これらの新しい値を使用して、対応するテンプレート パラメーターの値を置き換えます。  
  
## <a name="testing-the-template-parameter-substitution"></a>テンプレート パラメーターの置換のテスト  
 テンプレート パラメーターの置換をテストできます。  
  
#### <a name="to-test-the-template-parameter-substitution"></a>テンプレート パラメーターの置換をテストするには  
  
1. デバッグを開始し、実験用インスタンスで新しい SimpleProject を作成します。  
  
2. 内のブレークポイントで実行が停止、`AddFileFromTemplate`メソッド。  
  
3. 値を調べ、`nameSpace`と`className`パラメーター。  
  
   -   `nameSpace` 値が指定されて、 \<RootNamespace > \Templates\Projects\SimpleProject\SimpleProject.myproj プロジェクトのテンプレート ファイル内の要素。 ここでは、値は、"MyRootNamespace"です。  
  
   -   `className` ファイル名拡張子を除いた、クラスのソース ファイル名の値が指定されています。 この場合、最初のファイル変換先のフォルダーにコピーするのには、AssemblyInfo.cs;そのため、クラス名の値は、"AssemblyInfo"です。  
  
4. ブレークポイントを設定して、f5 キーを押して実行を続行します。  
  
    Visual Studio では、プロジェクトの作成を完了する必要があります。  
  
5. コード エディターで、Program.cs を開きます。 次のコードのようなソース コードが表示されます。  
  
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
  
    名前空間が"MyRootNamespace"こと、およびクラス名は、"Program"ことに注意してください。  
  
6. プロジェクトのデバッグを開始します。 新しいプロジェクトがコンパイル、実行、および「VSX こんにちは!!!」と表示 コンソール ウィンドウに表示します。  
  
    ![単純なプロジェクト コマンド](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
   おめでとうございます! マネージ プロジェクトは、基本的なシステムを実装しました。

