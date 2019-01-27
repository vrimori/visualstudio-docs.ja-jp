---
title: 基本的なプロジェクト システムの作成、パート 2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c4daab3ef0a045e1c352f170282db5e0189da3b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800049"
---
# <a name="create-a-basic-project-system-part-2"></a>基本的なプロジェクト システム、第 2 部を作成します。
このシリーズでは、最初のチュートリアル[基本的なプロジェクト システム、第 1 部作成](../extensibility/creating-a-basic-project-system-part-1.md)、基本的なプロジェクト システムを作成する方法を示しています。 このチュートリアルでは、Visual Studio テンプレート、プロパティ ページでは、その他の機能を追加して、基本的なプロジェクト システムに基づいています。 この 1 つを開始する前に、最初のチュートリアルを完了する必要がありま78す。  
  
 このチュートリアルでは、プロジェクト ファイル名拡張子を持つプロジェクトの種類を作成する方法を説明します *.myproj*します。 チュートリアルを完了するには、既存の Visual c# プロジェクト システムからでは、チュートリアルを利用するために、独自の言語を作成する必要はありません。  
  
 このチュートリアルでは、これらのタスクを実行する方法について説明します。  
  
-   Visual Studio テンプレートを作成します。  
  
-   Visual Studio テンプレートをデプロイします。  
  
-   プロジェクトの種類の子ノードを作成、**新しいプロジェクト** ダイアログ ボックス。  
  
-   Visual Studio テンプレートでパラメーター置換を有効にします。  
  
-   プロジェクトのプロパティ ページを作成します。  
  
> [!NOTE]
>  このチュートリアルの手順は、c# プロジェクトに基づいています。 ただし、ファイル名拡張子とコードなどの詳細を除く、Visual Basic プロジェクトと同じ手順を使用できます。  
  
## <a name="create-a-visual-studio-template"></a>Visual Studio テンプレートを作成します。  
 [基本的なプロジェクト システム、第 1 部作成](../extensibility/creating-a-basic-project-system-part-1.md)基本的なプロジェクト テンプレートを作成し、プロジェクト システムに追加する方法を示します。 Visual Studio でこのテンプレートを使用して登録する方法も示します、 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 、属性の完全なパスを書き込む、 *\\Templates\Projects\SimpleProject\\*システム内のフォルダーレジストリ。  
  
 Visual Studio テンプレートを使用して (*.vstemplate*ファイル)、基本的なプロジェクト テンプレートではなく、テンプレートでの表示方法を制御できます、**新しいプロジェクト** ダイアログ ボックスとテンプレートのパラメーターは代わりに使用します。  A *.vstemplate*ファイルはソース ファイルのプロジェクト システムのテンプレートを使用して、プロジェクトが作成されるときに含まれる方法を説明する XML ファイルです。 収集することで、プロジェクト システム自体が構築された、 *.vstemplate*ファイルとソース ファイルで、 *.zip*ファイルを開き、コピーすることによって展開されている、 *.zip*ファイルをある場所にVisual Studio に正常。 このプロセスは、このチュートリアルの後半で詳しく説明します。  
  
1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、に従って作成した SimpleProject ソリューションを開きます[基本的なプロジェクト システム、第 1 部作成](../extensibility/creating-a-basic-project-system-part-1.md)です。  
  
2. *SimpleProjectPackage.cs*ファイル、ProvideProjectFactory 属性を検索します。 2 番目のパラメーター (プロジェクト名) で、null、および 4 番目のパラメーター (プロジェクト テンプレート フォルダーへのパス) に置き換えます"。\\\NullPath"次のようにします。  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. という名前の XML ファイルを追加*SimpleProject.vstemplate*を*\\Templates\Projects\SimpleProject\\*フォルダー。  
  
4. 内容を置き換える*SimpleProject.vstemplate*を次のコード。  
  
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
  
5. **プロパティ**ウィンドウで、内のすべての 5 つのファイルを選択、 *\\Templates\Projects\SimpleProject\\*フォルダーと設定、**ビルド アクション****ZipProject**します。  
  
   ![単純なプロジェクト フォルダー](../extensibility/media/simpproj2.png "SimpProj2")  
  
   \<TemplateData > セクションは、SimpleProject プロジェクトの種類の外観と場所を決定します。、**新しいプロジェクト** ダイアログ ボックスで、次のようにします。  
  
- \<名 > 要素は SimpleProject アプリケーション プロジェクト テンプレートの名前します。  
  
- \<説明 > 要素に表示される説明が含まれています、**新しいプロジェクト**ダイアログ ボックスのプロジェクト テンプレートが選択されているとします。  
  
- \<アイコン > 要素を SimpleProject プロジェクトの種類と共に表示されるアイコンを指定します。  
  
- \<ProjectType > 要素の名前でプロジェクトの種類、**新しいプロジェクト** ダイアログ ボックス。 この名前は、ProvideProjectFactory 属性のプロジェクトの name パラメーターを置き換えます。  
  
  > [!NOTE]
  >  \<ProjectType > 要素に一致する必要があります、`LanguageVsTemplate`の引数、 `ProvideProjectFactory` SimpleProjectPackage.cs ファイル内の属性。  
  
  \<TemplateContent > セクションには、新しいプロジェクトが作成されるときに生成されるこれらのファイルがについて説明します。  
  
- *SimpleProject.myproj*  
  
- *Program.cs*  
  
- *AssemblyInfo.cs*  
  
  次の 3 つのすべてのファイルが`ReplaceParameters`true で、パラメーター置換を有効に設定します。  *Program.cs*ファイルが`OpenInEditor`プロジェクトを作成するときに、コード エディターで開くファイルを true に設定します。  
  
  Visual Studio テンプレート スキーマの要素の詳細については、次を参照してください。、 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)します。  
  
> [!NOTE]
>  プロジェクトには、複数の Visual Studio テンプレートがある場合は、すべてのテンプレートは、別のフォルダーには。 そのフォルダー内のすべてのファイルがあります、**ビルド アクション**設定**ZipProject**します。  
  
## <a name="adding-a-minimal-vsct-file"></a>最小限の .vsct ファイルを追加します。  
 Visual Studio は、新しいまたは変更された Visual Studio のテンプレートを認識するセットアップ モードで実行する必要があります。 セットアップ モードが必要です、 *.vsct*存在するファイル。 最小構成を追加する必要がありますそのため、 *.vsct*ファイルをプロジェクトにします。  
  
1.  という名前の XML ファイルを追加*SimpleProject.vsct* SimpleProject プロジェクトへです。  
  
2.  内容を置き換える、 *SimpleProject.vsct*を次のコード ファイル。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  設定、**ビルド アクション**するには、このファイルの**VSCTCompile**します。 これを行うだけで、 *.csproj*ファイルではなく、**プロパティ**ウィンドウ。 確認、**ビルド アクション**のこのファイルに設定されて**None**この時点でします。  
  
    1.  SimpleProject ノードを右クリックし、**編集 SimpleProject.csproj**します。  
  
    2.  *.Csproj*を探し、ファイル、 *SimpleProject.vsct*項目。  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  ビルドのアクションを変更する**VSCTCompile**します。  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  プロジェクト ファイルと、エディターを閉じます。  
  
    5.  SimpleProject ノードを保存し、、**ソリューション エクスプ ローラー**クリックして**プロジェクトの再読み込み**します。  
  
## <a name="examine-the-visual-studio-template-build-steps"></a>Visual Studio テンプレートのビルド手順を確認します。  
 VSPackage プロジェクトのビルド システムは、セットアップ モードでの Visual Studio を通常実行されるときに、 *.vstemplate*ファイルが変更されたか、プロジェクトを含む、 *.vstemplate*ファイルが再構築します。 Normal またはそれ以降、MSBuild の詳細レベルを設定して理解できます。  
  
1. **[ツール]** メニューの **[オプション]** をクリックします。  
  
2. 展開、**プロジェクトおよびソリューション**ノードをクリックして**をビルドおよび実行**します。  
  
3. 設定**MSBuild プロジェクト ビルドの出力の詳細**に**標準**します。 **[OK]** をクリックします。  
  
4. SimpleProject プロジェクトをリビルドします。  
  
   作成するビルド ステップ、 *.zip*プロジェクト ファイル例を次のようになります。  
  
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
  
## <a name="deploy-a-visual-studio-template"></a>Visual Studio テンプレートをデプロイします。  
 Visual Studio のテンプレートでは、パス情報は含まれません。 そのため、テンプレート *.zip*ファイルは、Visual Studio に認識されている場所にデプロイする必要があります。 ProjectTemplates フォルダーの場所は、通常 *< %localappdata% > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates*します。  
  
 プロジェクト ファクトリをデプロイするには、インストール プログラムは、管理者特権が必要です。 Visual Studio のインストールのノードの下のテンプレートをデプロイします。 *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*します。  
  
## <a name="test-a-visual-studio-template"></a>Visual Studio テンプレートをテストします。  
 Visual Studio テンプレートを使用して、プロジェクト階層を作成し、かどうかをプロジェクト ファクトリをテストします。  
  
1. Visual Studio SDK 実験用インスタンスをリセットします。  
  
    [!INCLUDE[win7](../debugger/includes/win7_md.md)]:**開始** メニューの 検索、 **Microsoft Visual Studio または Microsoft Visual Studio SDK/Tools**フォルダー、および選択**MicrosoftVisualStudio実験用インスタンスのリセット**.  
  
    以降のバージョンの Windows では。**開始**画面で「 **Microsoft Visual Studio をリセット\<バージョン > 実験用インスタンス**します。  
  
2. コマンド プロンプト ウィンドウが表示されます。 単語が表示されたら**任意のキーを押して続行**、 をクリックして**ENTER**します。 ウィンドウを閉じた後は、Visual Studio を開きます。  
  
3. SimpleProject プロジェクトをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
4. 実験用インスタンスの SimpleProject プロジェクトを作成します。 **新しいプロジェクト**ダイアログ ボックスで、 **SimpleProject**します。  
  
5. SimpleProject の新しいインスタンスを表示する必要があります。  
  
   ![単純なプロジェクトの新しいインスタンス](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")  
  
   ![プロジェクトの新しいインスタンス](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")  
  
## <a name="create-a-project-type-child-node"></a>プロジェクトの種類の子ノードを作成します。  
 プロジェクトの種類のノードに子ノードを追加することができます、**新しいプロジェクト** ダイアログ ボックス。  たとえば、SimpleProject プロジェクトの種類のコンソール アプリケーション、ウィンドウのアプリケーション、web アプリケーション、およびなどの子ノードがある可能性があります。  
  
 子ノード、プロジェクト ファイルを変更および追加で作成されます\<OutputSubPath > の子、 \<ZipProject > 要素。 ビルドまたは配置中に、テンプレートがコピーされると、すべての子ノードは、プロジェクト テンプレート フォルダーのサブフォルダーになります。  
  
 このセクションでは、SimpleProject プロジェクトの種類のコンソールの子ノードを作成する方法を示します。  
  
1.  名前の変更、 *\\Templates\Projects\SimpleProject\\*フォルダー  *\\Templates\Projects\ConsoleApp\\*します。  
  
2.  **プロパティ**ウィンドウで、内のすべての 5 つのファイルを選択、 *\\Templates\Projects\ConsoleApp\\*フォルダーを確認、**ビルド アクション**に設定されている**ZipProject**します。  
  
3.  SimpleProject.vstemplate ファイルの末尾に次の行を追加、 \<TemplateData > 終了タグの直前のセクション。  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     これにより、コンソール アプリケーション テンプレートをコンソールの子ノードと子ノードの 1 つである SimpleProject 親ノードの両方を表示します。  
  
4.  保存、 *SimpleProject.vstemplate*ファイル。  
  
5.  *.Csproj*ファイルを追加\<OutputSubPath > ZipProject 要素のそれぞれにします。 以前のように、プロジェクトをアンロードし、プロジェクト ファイルを編集します。  
  
6.  検索、 \<ZipProject > 要素。 各\<ZipProject > 要素を追加、 \<OutputSubPath > 要素コンソールの値を指定するとします。 ZipProject  
  
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
  
7.  この追加\<PropertyGroup > プロジェクト ファイル。  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  プロジェクト ファイルを保存し、プロジェクトの再読み込みします。  
  
## <a name="test-the-project-type-child-node"></a>プロジェクトの種類の子ノードをテストします。  
 変更されたプロジェクト ファイルをテストするかどうか、**コンソール**子ノードに表示されます、**新しいプロジェクト** ダイアログ ボックス。  
  
1. 実行、 **Microsoft Visual Studio の実験用インスタンスをリセット**ツール。  
  
2. SimpleProject プロジェクトをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
3. **新しいプロジェクト**ダイアログ ボックスで、をクリックして、 **SimpleProject**ノード。 **コンソール アプリケーション**テンプレートを表示する必要があります、**テンプレート**ウィンドウ。  
  
4. 展開、 **SimpleProject**ノード。 **コンソール**子ノードが表示されます。 **SimpleProject アプリケーション**テンプレートに引き続き表示されます、**テンプレート**ウィンドウ。  
  
5. クリックして**キャンセル**デバッグを停止します。  
  
   ![単純なプロジェクト ロールアップ](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")  
  
   ![単純なプロジェクト コンソール ノード](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substitute-project-template-parameters"></a>プロジェクト テンプレートのパラメーターを置き換える  
 [基本的なプロジェクト システムを作成するには、パート 1](../extensibility/creating-a-basic-project-system-part-1.md)を上書きする方法を示しました、`ProjectNode.AddFileFromTemplate`メソッドをテンプレート パラメーター置換の基本的な種類の操作を行います。 このセクションより高度な Visual Studio テンプレートのパラメーターを使用する方法を説明します。  
  
 Visual Studio テンプレートを使用してプロジェクトを作成するときに、**新しいプロジェクト**ダイアログ ボックスで、プロジェクトをカスタマイズする文字列のテンプレートとパラメーターが置き換えられます。 テンプレート パラメーターは、始まり $time$ など、ドル記号で終了する特別なトークンです。 次の 2 つのパラメーターは、テンプレートに基づいてプロジェクトでカスタマイズを有効にするために特に便利です。  
  
- 1 ~ 10 $GUID$ は、新しい Guid に置き換えられます。 最大 10 個の一意な Guid guid1 $$ などを指定することができます。  
  
- $safeprojectname$ がユーザーによって指定された名前、**新しいプロジェクト** ダイアログ ボックスで、すべての安全でない文字とスペースを削除するように変更します。  
  
  テンプレート パラメーターの完全な一覧については、「[テンプレート パラメーター](../ide/template-parameters.md)」を参照してください。  
  
### <a name="to-substitute-project-template-parameters"></a>プロジェクト テンプレートのパラメーター値  
  
1.  *SimpleProjectNode.cs*ファイルで、削除、`AddFileFromTemplate`メソッド。  
  
2.  *\\Templates\Projects\ConsoleApp\SimpleProject.myproj*を探し、ファイル、 \<RootNamespace > プロパティ $safeprojectname$ にその値を変更します。  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  *\\Templates\Projects\SimpleProject\Program.cs*ファイルで、ファイルの内容を次のコードに置き換えます。  
  
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
  
5.  新しい SimpleProject コンソール アプリケーションを作成します。 (で、**プロジェクトの種類**ペインで、 **SimpleProject**します。 **Visual Studio にインストールされたテンプレート**、**コンソール アプリケーション**)。  
  
6.  新しく作成されたプロジェクトで開く*Program.cs*します。 次のように表示されます (、ファイルの GUID 値は異なります。)。  
  
    ```csharp  
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
  
## <a name="create-a-project-property-page"></a>プロジェクト プロパティ ページを作成します。  
 種類のプロジェクト プロパティ ページを作成するには、ユーザーを表示し、テンプレートに基づくプロジェクトのプロパティを変更することができます。 このセクションでは、構成に依存しないプロパティ ページを作成する方法を示します。 この基本的なプロパティ ページでは、プロパティ グリッドを使用して、プロパティ ページ クラスで公開されるパブリック プロパティを表示します。  
  
 プロパティ ページ クラスを派生、`SettingsPage`基本クラス。 によって提供されるプロパティ グリッド、`SettingsPage`クラスはほとんどのプリミティブ データ型を認識し、それらを表示する方法を認識します。  さらに、`SettingsPage`クラスは、プロジェクト ファイルにプロパティ値を保持する方法を認識します。  
  
 このセクションで作成するプロパティ ページでは、alter、およびこれらのプロジェクト プロパティを保存できます。  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace します。  
  
1. *SimpleProjectPackage.cs*ファイルに、この追加`ProvideObject`属性を`SimpleProjectPackage`クラス。  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    これは、プロパティ ページ クラスを登録します`GeneralPropertyPage`com。  
  
2. *SimpleProjectNode.cs*ファイルで、これら 2 つのオーバーライドされたメソッドを追加、`SimpleProjectNode`クラス。  
  
   ```csharp  
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
  
    これら両方のメソッドは、プロパティ ページ Guid の配列を返します。  GeneralPropertyPage GUID は、配列内の唯一の要素、**プロパティ ページ** ダイアログ ボックスが 1 つだけのページに表示されます。  
  
3. という名前のクラス ファイルを追加*GeneralPropertyPage.cs* SimpleProject プロジェクトへです。  
  
4. 次のコードを使用してこのファイルの内容に置き換えます。  
  
   ```csharp  
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
  
    `GeneralPropertyPage`クラスは、AssemblyName、OutputType、および RootNamespace は、次の 3 つのパブリック プロパティを公開します。 AssemblyName に set メソッドがあるないために、読み取り専用プロパティとして表示されます。 OutputType は列挙型の定数は、ドロップダウン リストとして表示されます。  
  
    `SettingsPage`基底クラスを提供します`ProjectMgr`プロパティを保持します。 `BindProperties`メソッドは`ProjectMgr`を永続化されたプロパティの値を取得し、対応するプロパティを設定します。  `ApplyChanges`メソッドは`ProjectMgr`プロパティの値を取得し、プロジェクト ファイルに保存します。 プロパティ設定メソッドのセット`IsDirty`プロパティを永続化する必要があることを指定する場合は true にします。  永続化は、プロジェクトまたはソリューションを保存するときに発生します。  
  
5. SimpleProject ソリューションをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
6. 実験用のインスタンスでは、新しい SimpleProject アプリケーションを作成します。  
  
7. Visual Studio では、Visual Studio テンプレートを使用してプロジェクトを作成する、プロジェクト ファクトリを呼び出します。 新しい*Program.cs*ファイルがコード エディターで開きます。  
  
8. プロジェクト ノードを右クリックして**ソリューション エクスプ ローラー**、 をクリックし、**プロパティ**します。 **[プロパティ ページ]** ダイアログ ボックスが表示されます。  
  
   ![単純なプロジェクト プロパティ ページ](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")  
  
## <a name="test-the-project-property-page"></a>テスト プロジェクトのプロパティ ページ
 ここで変更してプロパティ値を変更するかどうかをテストできます。  
  
1. **MyConsoleApplication プロパティ ページ** ダイアログ ボックスで、変更、 **DefaultNamespace**に**MyApplication**します。  
  
2. 選択、 **OutputType**プロパティ、および選択**クラス ライブラリ**します。  
  
3. クリックして**適用**、順にクリックします**OK**します。  
  
4. 再度、**プロパティ ページ** ダイアログ ボックスし、変更が保存されていることを確認します。  
  
5. Visual Studio の実験用インスタンスを終了します。  
  
6. 実験用インスタンスをもう一度開きます。  
  
7. 再度、**プロパティ ページ** ダイアログ ボックスし、変更が保存されていることを確認します。  
  
8. Visual Studio の実験用インスタンスを終了します。  
  
   ![実験用インスタンスを閉じて](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
