---
title: "基本的なプロジェクト システムを作成するには、パート 2 |Microsoft ドキュメント"
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
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 699f9176fd39cacaf2bb4f433cd9d2ceb8e326b5
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="creating-a-basic-project-system-part-2"></a>基本的なプロジェクト システムを作成するには、パート 2
このシリーズの最初のチュートリアル[基本プロジェクト システムでは、第 1 部を作成する](../extensibility/creating-a-basic-project-system-part-1.md)、基本的なプロジェクト システムを作成する方法を示します。 このチュートリアルでは、Visual Studio のテンプレート、プロパティ ページ、およびその他の機能を追加することで、基本的なプロジェクト システムに基づいています。 この 1 つを開始する前に、最初のチュートリアルを完了する必要があります。  
  
 このチュートリアルでは、プロジェクト ファイル名拡張子 .myproj のあるプロジェクトの種類を作成する方法を説明します。 このチュートリアルを完了するには、チュートリアルは、既存の Visual c# プロジェクト システムから借用するために、独自の言語を作成する必要はありません。  
  
 このチュートリアルでこれらのタスクを実行する方法について説明します。  
  
-   Visual Studio のテンプレートを作成します。  
  
-   Visual Studio のテンプレートを展開します。  
  
-   プロジェクトの種類の子ノードを作成、**新しいプロジェクト** ダイアログ ボックス。  
  
-   Visual Studio のテンプレートでパラメーター置換を有効にします。  
  
-   プロジェクトのプロパティ ページを作成します。  
  
> [!NOTE]
>  このチュートリアルの手順では、c# プロジェクトに基づきます。 ただし、ファイル名拡張子とコードなどの詳細を除く、Visual Basic プロジェクトと同じ手順を使用できます。  
  
## <a name="creating-a-visual-studio-template"></a>Visual Studio テンプレートの作成  
 [基本的なプロジェクト システムでは、第 1 部を作成する](../extensibility/creating-a-basic-project-system-part-1.md)基本的なプロジェクト テンプレートを作成し、プロジェクト システムに追加する方法を示します。 使用して、このテンプレートを Visual Studio に登録する方法も示しています、<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>属性は、システム レジストリの \Templates\Projects\SimpleProject\ フォルダーの完全なパスを書き込みます。  
  
 Visual Studio のテンプレート (.vstemplate ファイル) を使用すると、基本的なプロジェクト テンプレートではなくでのテンプレートの表示方法を制御できます、**新しいプロジェクト** ダイアログ ボックスとテンプレート パラメーターが次のように置き換えられます。  .Vstemplate ファイルは、ソース ファイルのプロジェクト システム テンプレートを使用して、プロジェクトが作成されるときに含まれる方法を記述する XML ファイルです。 プロジェクト システム自体は、.vstemplate ファイルとファイルは .zip ファイル内のソース ファイルを収集してビルドされ、Visual Studio に認識されている場所に .zip ファイルをコピーして配置します。 このプロセスは、このチュートリアルの後半で詳しく説明します。  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、に従って作成した SimpleProject ソリューションを開く[基本プロジェクト システムでは、第 1 部を作成する](../extensibility/creating-a-basic-project-system-part-1.md)です。  
  
2.  SimpleProjectPackage.cs ファイルの検索、ProvideProjectFactory 属性。 Null、2 番目のパラメーター (プロジェクト名) と 4 番目のパラメーター (プロジェクト テンプレート フォルダーへのパス) で置き換えられます"。\\\NullPath"次のようにします。  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
        ".\\NullPath",  
    LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  SimpleProject.vstemplate \Templates\Projects\SimpleProject\ フォルダーに名前の付いた XML ファイルを追加します。  
  
4.  SimpleProject.vstemplate の内容を次のコードに置き換えます。  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
      <TemplateData>  
        <Name>SimpleProject Application</Name>  
        <Description>  
            A project for creating a SimpleProject application  
         </Description>  
         <Icon>SimpleProject.ico</Icon>  
         <ProjectType>SimpleProject</ProjectType>  
      </TemplateData>  
      <TemplateContent>  
        <Project File="SimpleProject.myproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
              Program.cs  
          </ProjectItem>  
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">  
             AssemblyInfo.cs  
          </ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
5.  **プロパティ**ウィンドウで、\Templates\Projects\SimpleProject\ フォルダーとセット内のすべての 5 のファイルを選択、**ビルド アクション**に**ZipProject**です。  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 \<TemplateData > セクション SimpleProject プロジェクトの種類の外観と場所を決定する、**新しいプロジェクト**ダイアログ ボックスで、次のようにします。  
  
-   \<名 > 要素を SimpleProject アプリケーション プロジェクト テンプレートの名前します。  
  
-   \<説明 > 要素が含まれている説明を表す、**新しいプロジェクト**ダイアログ ボックスのプロジェクト テンプレートが選択されているとします。  
  
-   \<アイコン > 要素が SimpleProject プロジェクトの種類と共に表示されるアイコンを指定します。  
  
-   \<ProjectType > 要素の名前でプロジェクトの種類、**新しいプロジェクト** ダイアログ ボックス。 この名前は、プロジェクトの name パラメーター ProvideProjectFactory 属性を置き換えます。  
  
    > [!NOTE]
    >  \<ProjectType > 要素に一致する必要があります、`LanguageVsTemplate`の引数、 `ProvideProjectFactory` SimpleProjectPackage.cs ファイル内の属性です。  
  
 \<TemplateContent > セクションでは、新しいプロジェクトが作成されるときに生成されるこれらのファイルをについて説明します。  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   AssemblyInfo.cs  
  
 次の 3 つのすべてのファイルが`ReplaceParameters`true で、パラメーター置換を有効に設定します。  Program.cs ファイルに`OpenInEditor`true の場合、これにより、プロジェクトを作成すると、コード エディターで開かれるファイルに設定します。  
  
 Visual Studio テンプレート スキーマの要素の詳細については、次を参照してください。、 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)です。  
  
> [!NOTE]
>  プロジェクトに 1 つ以上の Visual Studio テンプレートがある場合は、すべてのテンプレートは、別のフォルダーです。 そのフォルダー内のすべてのファイルが必要、**ビルド アクション**'éý' **ZipProject**です。  
  
## <a name="adding-a-minimal-vsct-file"></a>最小限の .vsct ファイルを追加します。  
 Visual Studio は、新しいまたは変更された Visual Studio のテンプレートを認識するようにセットアップ モードで実行する必要があります。 セットアップ モードには、存在する .vsct ファイルが必要です。 そのため、プロジェクトに最低限の .vsct ファイルを追加する必要があります。  
  
1.  SimpleProject.vsct SimpleProject プロジェクトに名前の付いた XML ファイルを追加します。  
  
2.  SimpleProject.vsct ファイルの内容を次のコードに置き換えます。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  設定、**ビルド アクション**するには、このファイルの**VSCTCompile**です。 これを行う、.csproj ファイルでのみではなく、**プロパティ**ウィンドウです。 確認して、**ビルド アクション**のこのファイルに設定されている**None**この時点でします。  
  
    1.  SimpleProject ノードを右クリックし、をクリックして**編集 SimpleProject.csproj**です。  
  
    2.  .Csproj ファイルでは、SimpleProject.vsct アイテムを探します。  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  ビルドのアクションを変更する**VSCTCompile**です。  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  プロジェクト ファイルと、エディターを閉じます。  
  
    5.  SimpleProject ノードを保存し、次に、**ソリューション エクスプ ローラー**クリックして**プロジェクトの再読み込み**です。  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Visual Studio テンプレートのビルド ステップを確認します。  
 VSPackage プロジェクトのビルド システムは、.vstemplate ファイルが変更されたか、.vstemplate ファイルを含むプロジェクトがリビルドされるときに通常 Visual Studio とセットアップ モードで実行されます。 Normal またはそれ以降は、MSBuild の詳細レベルを設定していくことができます。  
  
1.  **[ツール]** メニューの **[オプション]**をクリックします。  
  
2.  展開、**プロジェクトおよびソリューション**ノードをクリックして**ビルドおよび実行する**です。  
  
3.  設定**MSBuild プロジェクトのビルド出力の詳細度**に**標準**です。 **[OK]**をクリックします。  
  
4.  SimpleProject プロジェクトをリビルドします。  
  
 .Zip プロジェクト ファイルを作成するビルド ステップは、次の例のようになります。  
  
```  
ZipProjects:  
1>  Zipping ProjectTemplates  
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".  
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip  
1>ZipItems:  
1>  Zipping ItemTemplates  
1>  SimpleProject ->  
```  
  
## <a name="deploying-a-visual-studio-template"></a>Visual Studio テンプレートを展開します。  
 Visual Studio のテンプレートでは、パス情報は含まれません。 そのため、Visual Studio に認識されている場所にテンプレート .zip ファイルを展開する必要があります。 ProjectTemplates フォルダーの場所は、通常 **\<%localappdata% > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**です。  
  
 インストール プログラムは、プロジェクト ファクトリを展開するには、管理者特権が必要です。 テンプレート [Visual Studio のインストール] ノードを展開します。 **...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates**です。  
  
## <a name="testing-a-visual-studio-template"></a>Visual Studio テンプレートのテスト  
 Visual Studio テンプレートを使用して、プロジェクト階層を作成するかどうかを表示する、プロジェクト ファクトリをテストします。  
  
1.  Visual Studio SDK の実験用インスタンスをリセットします。  
  
     [!INCLUDE[win7](../debugger/includes/win7_md.md)]: [スタート] メニューで、検索、 **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools**フォルダー、および選択**Microsoft Visual Studio 実験用インスタンスをリセット**です。  
  
     以降のバージョンの Windows: [スタート] 画面で、型**Microsoft Visual Studio をリセット\<バージョン > 実験用インスタンス**です。  
  
2.  コマンド プロンプト ウィンドウが表示されます。 単語が表示されている場合`Press any key to continue`、enter キーを押します。 ウィンドウを閉じた後は、Visual Studio を開きます。  
  
3.  SimpleProject プロジェクトをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
4.  実験用インスタンスの SimpleProject プロジェクトを作成します。 **新しいプロジェクト**ダイアログ ボックスで、 **SimpleProject**です。  
  
5.  SimpleProject の新しいインスタンスを表示する必要があります。  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>プロジェクトの種類の子ノードを作成します。  
 プロジェクトの種類のノードに子ノードを追加することができます、**新しいプロジェクト** ダイアログ ボックス。  たとえば、SimpleProject プロジェクトの種類のコンソール アプリケーション、ウィンドウのアプリケーション、web アプリケーション、およびなどの子ノードをことができます。  
  
 子ノードは、プロジェクト ファイルを変更し、追加することによって作成された\<OutputSubPath > の子、 \<ZipProject > 要素。 ビルドまたは配置中に、テンプレートをコピーすると、すべての子ノードは、プロジェクト テンプレート フォルダーのサブフォルダーになります。  
  
 このセクションでは、コンソール SimpleProject プロジェクトの種類の子ノードを作成する方法を示します。  
  
1.  \Templates\Projects\SimpleProject\ フォルダーの名前を \Templates\Projects\ConsoleApp\\です。  
  
2.  **プロパティ**ウィンドウで、\Templates\Projects\ConsoleApp\ フォルダー内のすべての 5 つのファイルを選択し、確認、**ビルド アクション**に設定されている**ZipProject**です。  
  
3.  SimpleProject.vstemplate ファイルの末尾に次の行を追加、 \<TemplateData > セクションでは、終了タグの直前にします。  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     これにより、コンソール アプリケーション テンプレートをコンソールの子ノードとすると、SimpleProject 親ノードの子ノード上の 1 つのレベルの両方を表示します。  
  
4.  SimpleProject.vstemplate ファイルを保存します。  
  
5.  .Csproj ファイルで追加\<OutputSubPath > ZipProject 要素のそれぞれにします。 以前のように、プロジェクトをアンロードし、プロジェクト ファイルを編集します。  
  
6.  検索、 \<ZipProject > 要素。 それぞれに\<ZipProject > 要素を追加、 \<OutputSubPath > 要素コンソール値を指定するとします。 ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>  
    ```  
  
7.  この追加\<PropertyGroup > をプロジェクト ファイル。  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  プロジェクト ファイルを保存し、プロジェクトの再読み込みします。  
  
## <a name="testing-the-project-type-child-node"></a>プロジェクトの種類の子ノードのテスト  
 変更されたプロジェクトを表示するファイルをテストするかどうか、**コンソール**子ノードに表示されます、**新しいプロジェクト** ダイアログ ボックス。  
  
1.  実行、 **Microsoft Visual Studio の実験用インスタンスをリセット**ツールです。  
  
2.  SimpleProject プロジェクトをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
3.  **新しいプロジェクト**ダイアログ ボックスで、をクリックして、 **SimpleProject**ノード。 **コンソール アプリケーション**テンプレートを表示する必要があります、**テンプレート**ウィンドウです。  
  
4.  展開して、 **SimpleProject**ノード。 **コンソール**子ノードが表示されます。 **SimpleProject アプリケーション**テンプレートに引き続き表示されます、**テンプレート**ウィンドウです。  
  
5.  である必要があります。 をクリックして**キャンセル**およびデバッグの停止  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>プロジェクト テンプレートのパラメーターの置換  
 [基本的なプロジェクト システムでは、第 1 部を作成する](../extensibility/creating-a-basic-project-system-part-1.md)を上書きする方法を示しました、`ProjectNode.AddFileFromTemplate`メソッドをテンプレート パラメーター置換の基本的な種類の操作を行います。 このセクションより高度な Visual Studio のテンプレート パラメーターを使用する方法を説明します。  
  
 Visual Studio テンプレートを使用して、プロジェクトを作成する場合、**新しいプロジェクト**ダイアログ ボックスで、プロジェクトをカスタマイズする文字列をテンプレート パラメーターが置き換えられます。 テンプレート パラメーターは、特別なトークンを開始し、たとえば、$time$ がドル記号で終了します。 次の 2 つのパラメーターは、テンプレートに基づいてプロジェクトでカスタマイズを有効にするために特に便利です。  
  
-   1 ~ 10 の $GUID$ は、新しい Guid に置き換えられます。 最大 10 の Guid、guid1 $$ などを指定できます。  
  
-   $safeprojectname$ がユーザーによって指定された名前、**新しいプロジェクト**ダイアログ ボックスで、安全でない文字とスペースをすべて削除するように変更します。  
  
 テンプレート パラメーターの完全な一覧については、「[テンプレート パラメーター](../ide/template-parameters.md)」をご覧ください。  
  
#### <a name="to-substitute-project-template-parameters"></a>プロジェクト テンプレートのパラメーターを置換するには  
  
1.  SimpleProjectNode.cs ファイルの削除、`AddFileFromTemplate`メソッドです。  
  
2.  \Templates\Projects\ConsoleApp\SimpleProject.myproj ファイルで探します、 \<RootNamespace > プロパティ $safeprojectname$ をその値を変更します。  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  \Templates\Projects\SimpleProject\Program.cs ファイル内のファイルの内容を次のコードに置き換えます。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace $safeprojectname$  
    {  
        [Guid("$guid1$")]  
        public class $safeprojectname$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
4.  SimpleProject プロジェクトをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
5.  新しい SimpleProject コンソール アプリケーションを作成します。 (で、**プロジェクトの種類**ペインで、 **SimpleProject**です。 **Visual Studio にインストールされたテンプレート****コンソール アプリケーション**)。  
  
6.  新しく作成されたプロジェクトで Program.cs を開きます。 次のような項目が表示されます (、ファイルの GUID 値が異なります。)。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace Console_Application1  
    {  
        [Guid("00000000-0000-0000-00000000-00000000)"]  
        public class Console_Application1  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
## <a name="creating-a-project-property-page"></a>プロジェクト プロパティ ページを作成します。  
 ユーザーを表示し、テンプレートに基づいてプロジェクトのプロパティを変更するために、プロジェクトの種類のプロパティ ページを作成できます。 このセクションでは、構成に依存しないプロパティ ページを作成する方法を示します。 この基本的なプロパティ ページでは、プロパティ グリッドを使用して、プロパティ ページ クラスで公開するパブリック プロパティを表示します。  
  
 クラスのプロパティ ページから、`SettingsPage`基本クラスです。 によって提供されるプロパティ グリッド、`SettingsPage`クラスがほとんどのプリミティブ データ型を認識しており、それらを表示する方法を認識します。  さらに、`SettingsPage`クラスは、プロジェクト ファイルにプロパティ値を保持する方法を認識しています。  
  
 このセクションの内容を作成するプロパティ ページでは、alter、およびこれらのプロジェクト プロパティを保存できます。  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace です。  
  
1.  SimpleProjectPackage.cs ファイルでこれを追加`ProvideObject`属性を`SimpleProjectPackage`クラス。  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))]  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     これにより、プロパティ ページ クラスが登録`GeneralPropertyPage`com  
  
2.  SimpleProjectNode.cs ファイル内に 2 つのオーバーライドされたメソッドを追加、`SimpleProjectNode`クラス。  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
        return result;  
    }  
    protected override Guid[] GetPriorityProjectDesignerPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
         return result;  
    }  
    ```  
  
     これら両方のメソッドは、プロパティ ページ Guid の配列を返します。  GeneralPropertyPage GUID は、配列内の唯一の要素をため、**プロパティ ページ**ダイアログ ボックスは 1 ページのみを表示します。  
  
3.  SimpleProject プロジェクトに GeneralPropertyPage.cs をという名前のクラス ファイルを追加します。  
  
4.  次のコードを使用してこのファイルの内容を置き換えます。  
  
    ```  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Project;  
    using System.ComponentModel;  
  
    namespace SimpleProject  
    {  
        [ComVisible(true)]  
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]  
        public class GeneralPropertyPage : SettingsPage  
        {  
            private string assemblyName;  
            private OutputType outputType;  
            private string defaultNamespace;  
  
            public GeneralPropertyPage()  
            {  
                this.Name = "General";  
            }  
  
            [Category("AssemblyName")]  
            [DisplayName("AssemblyName")]  
            [Description("The output file holding assembly metadata.")]  
            public string AssemblyName  
            {  
                get { return this.assemblyName; }  
            }  
            [Category("Application")]  
            [DisplayName("OutputType")]  
            [Description("The type of application to build.")]  
            public OutputType OutputType  
            {  
                get { return this.outputType; }  
                set { this.outputType = value; this.IsDirty = true; }  
            }  
            [Category("Application")]  
            [DisplayName("DefaultNamespace")]  
            [Description("Specifies the default namespace for added items.")]  
            public string DefaultNamespace  
            {  
                get { return this.defaultNamespace; }  
                set { this.defaultNamespace = value; this.IsDirty = true; }  
            }  
  
            protected override void BindProperties()  
            {  
                this.assemblyName = this.ProjectMgr.GetProjectProperty(  
    "AssemblyName", true);  
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
    "RootNamespace", false);  
  
                string outputType = this.ProjectMgr.GetProjectProperty(  
    "OutputType", false);  
                this.outputType =   
    (OutputType)Enum.Parse(typeof(OutputType), outputType);  
            }  
  
            protected override int ApplyChanges()  
            {  
                this.ProjectMgr.SetProjectProperty(  
    "AssemblyName", this.assemblyName);  
                this.ProjectMgr.SetProjectProperty(  
    "OutputType", this.outputType.ToString());  
                this.ProjectMgr.SetProjectProperty(  
    "RootNamespace", this.defaultNamespace);  
                this.IsDirty = false;  
  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    ```  
  
     `GeneralPropertyPage`クラス AssemblyName、OutputType、および RootNamespace は、次の 3 つのパブリック プロパティを公開します。 AssemblyName に set メソッドがあるないために、読み取り専用プロパティとして表示されます。 OutputType は列挙型の定数は、ドロップダウン リストとして表示されます。  
  
     `SettingsPage`基本クラスを提供`ProjectMgr`プロパティを保持します。 `BindProperties`メソッドを使用`ProjectMgr`を永続化されたプロパティ値を取得し、対応するプロパティを設定します。  `ApplyChanges`メソッドを使用`ProjectMgr`プロパティの値を取得し、プロジェクト ファイルに保存します。 プロパティ メソッドのセットを設定する`IsDirty`プロパティを永続化する必要があることを示すために true にします。  永続化は、プロジェクトまたはソリューションを保存するときに発生します。  
  
5.  SimpleProject ソリューションをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
6.  実験用インスタンスの新しい SimpleProject アプリケーションを作成します。  
  
7.  Visual Studio では、Visual Studio テンプレートを使用してプロジェクトを作成する、プロジェクト ファクトリを呼び出します。 新しい Program.cs ファイルがコード エディターで開きます。  
  
8.  プロジェクト ノードを右クリックして**ソリューション エクスプ ローラー**、クリックして**プロパティ**です。 **[プロパティ ページ]** ダイアログ ボックスが表示されます。  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>プロジェクト プロパティ ページのテスト  
 今すぐ変更でき、プロパティ値を変更するかどうかをテストできます。  
  
1.  **MyConsoleApplication プロパティ ページ** ダイアログ ボックスで、変更、**に DefaultNamespace**に**MyApplication**です。  
  
2.  選択、 **OutputType**プロパティ、および選択**クラス ライブラリ**です。  
  
3.  をクリックして**適用**、順にクリック**OK**です。  
  
4.  再び開き、**プロパティ ページ** ダイアログ ボックスし、変更内容が永続化されていることを確認します。  
  
5.  Visual Studio の実験用インスタンスを終了します。  
  
6.  実験用インスタンスを再度開きます。  
  
7.  再び開き、**プロパティ ページ** ダイアログ ボックスし、変更内容が永続化されていることを確認します。  
  
8.  Visual Studio の実験用インスタンスを終了します。  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")