---
title: 基本的なプロジェクト システムの作成、パート 2 |Microsoft Docs
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
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58d456e9c6578ba36b8d4425238208a2435a6523
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859240"
---
# <a name="creating-a-basic-project-system-part-2"></a>基本的なプロジェクト システムの作成、パート 2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このシリーズでは、最初のチュートリアル[基本的なプロジェクト システムでは、第 1 部作成](../extensibility/creating-a-basic-project-system-part-1.md)、基本的なプロジェクト システムを作成する方法を示しています。 このチュートリアルでは、Visual Studio テンプレート、プロパティ ページでは、その他の機能を追加して、基本的なプロジェクト システムに基づいています。 この 1 つを開始する前に、最初のチュートリアルを完了する必要があります。  
  
 このチュートリアルでは、プロジェクト ファイル名拡張子 .myproj を含むプロジェクトの種類を作成する方法について説明します。 チュートリアルを完了するには、既存の Visual c# プロジェクト システムからでは、チュートリアルを利用するために、独自の言語を作成する必要はありません。  
  
 このチュートリアルでは、これらのタスクを実行する方法について説明します。  
  
-   Visual Studio テンプレートを作成します。  
  
-   Visual Studio テンプレートをデプロイします。  
  
-   プロジェクトの種類の子ノードを作成、**新しいプロジェクト** ダイアログ ボックス。  
  
-   Visual Studio テンプレートでパラメーター置換を有効にします。  
  
-   プロジェクトのプロパティ ページを作成します。  
  
> [!NOTE]
>  このチュートリアルの手順は、c# プロジェクトに基づいています。 ただし、ファイル名拡張子とコードなどの詳細を除く、Visual Basic プロジェクトと同じ手順を使用できます。  
  
## <a name="creating-a-visual-studio-template"></a>Visual Studio テンプレートを作成します。  
 [基本的なプロジェクト システムでは、第 1 部作成](../extensibility/creating-a-basic-project-system-part-1.md)基本的なプロジェクト テンプレートを作成し、プロジェクト システムに追加する方法を示します。 Visual Studio でこのテンプレートを使用して登録する方法も示します、<xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>属性には、\Templates\Projects\SimpleProject\ フォルダーの完全なパスをシステム レジストリに書き込みます。  
  
 Visual Studio テンプレート (.vstemplate ファイル) を使用すると、基本的なプロジェクト テンプレートではなく、テンプレートでの表示方法を制御できます、**新しいプロジェクト** ダイアログ ボックスし、どのテンプレート パラメーターに代入されます。  .Vstemplate ファイルは、ソース ファイルのプロジェクト システムのテンプレートを使用して、プロジェクトが作成されるときに含まれる方法を説明する XML ファイルです。 プロジェクト システム自体は、.vstemplate ファイルと、.zip ファイル内のソース ファイルを収集することでビルドされ、Visual Studio に認識されている場所に .zip ファイルをコピーして配置します。 このプロセスは、このチュートリアルの後半で詳しく説明します。  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、に従って作成した SimpleProject ソリューションを開きます[基本的なプロジェクト システムでは、第 1 部作成](../extensibility/creating-a-basic-project-system-part-1.md)です。  
  
2. SimpleProjectPackage.cs ファイルでは、ProvideProjectFactory 属性を検索します。 2 番目のパラメーター (プロジェクト名) で、null、および 4 番目のパラメーター (プロジェクト テンプレート フォルダーへのパス) に置き換えます"。\\\NullPath"次のようにします。  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. SimpleProject.vstemplate \Templates\Projects\SimpleProject\ フォルダーをという名前の XML ファイルを追加します。  
  
4. SimpleProject.vstemplate の内容を次のコードに置き換えます。  
  
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
  
5. **プロパティ**ウィンドウで、すべて 5 が \Templates\Projects\SimpleProject\ フォルダーとセット ファイルを選択、**ビルド アクション**に**ZipProject**します。  
  
   ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
   \<TemplateData > セクションは、SimpleProject プロジェクトの種類の外観と場所を決定します。、**新しいプロジェクト** ダイアログ ボックスで、次のようにします。  
  
- \<名 > 要素は SimpleProject アプリケーション プロジェクト テンプレートの名前します。  
  
- \<説明 > 要素に表示される説明が含まれています、**新しいプロジェクト**ダイアログ ボックスのプロジェクト テンプレートが選択されているとします。  
  
- \<アイコン > 要素を SimpleProject プロジェクトの種類と共に表示されるアイコンを指定します。  
  
- \<ProjectType > 要素の名前でプロジェクトの種類、**新しいプロジェクト** ダイアログ ボックス。 この名前は、ProvideProjectFactory 属性のプロジェクトの name パラメーターを置き換えます。  
  
  > [!NOTE]
  >  \<ProjectType > 要素に一致する必要があります、`LanguageVsTemplate`の引数、 `ProvideProjectFactory` SimpleProjectPackage.cs ファイル内の属性。  
  
  \<TemplateContent > セクションには、新しいプロジェクトが作成されるときに生成されるこれらのファイルがについて説明します。  
  
- SimpleProject.myproj  
  
- Program.cs  
  
- AssemblyInfo.cs  
  
  次の 3 つのすべてのファイルが`ReplaceParameters`true で、パラメーター置換を有効に設定します。  Program.cs ファイルが`OpenInEditor`プロジェクトを作成するときに、コード エディターで開くファイルを true に設定します。  
  
  Visual Studio テンプレート スキーマの要素の詳細については、次を参照してください。、 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)します。  
  
> [!NOTE]
>  プロジェクトには、複数の Visual Studio テンプレートがある場合は、すべてのテンプレートは、別のフォルダーには。 そのフォルダー内のすべてのファイルがあります、**ビルド アクション**設定**ZipProject**します。  
  
## <a name="adding-a-minimal-vsct-file"></a>最小限の .vsct ファイルを追加します。  
 Visual Studio は、新しいまたは変更された Visual Studio のテンプレートを認識するセットアップ モードで実行する必要があります。 セットアップ モードでは、.vsct ファイルが存在する必要があります。 したがって、プロジェクトに最小限の .vsct ファイルを追加する必要があります。  
  
1.  SimpleProject.vsct SimpleProject プロジェクトをという名前の XML ファイルを追加します。  
  
2.  SimpleProject.vsct ファイルの内容を次のコードに置き換えます。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  設定、**ビルド アクション**するには、このファイルの**VSCTCompile**します。 これを .csproj ファイルでのみではなく、**プロパティ**ウィンドウ。 確認、**ビルド アクション**のこのファイルに設定されて**None**この時点でします。  
  
    1.  SimpleProject ノードを右クリックし、**編集 SimpleProject.csproj**します。  
  
    2.  .Csproj ファイルでは、SimpleProject.vsct アイテムを探します。  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  ビルドのアクションを変更する**VSCTCompile**します。  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  プロジェクト ファイルと、エディターを閉じます。  
  
    5.  SimpleProject ノードを保存し、、**ソリューション エクスプ ローラー**クリックして**プロジェクトの再読み込み**します。  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Visual Studio テンプレートのビルド ステップを調べる  
 VSPackage プロジェクトのビルド システムは、.vstemplate ファイルが変更されたか、.vstemplate ファイルを含むプロジェクトが再構築時に通常 Visual Studio とセットアップ モードで実行されます。 Normal またはそれ以降、MSBuild の詳細レベルを設定して理解できます。  
  
1. **[ツール]** メニューの **[オプション]** をクリックします。  
  
2. 展開、**プロジェクトおよびソリューション**ノードをクリックして**をビルドおよび実行**します。  
  
3. 設定**MSBuild プロジェクト ビルドの出力の詳細**に**標準**します。 **[OK]** をクリックします。  
  
4. SimpleProject プロジェクトをリビルドします。  
  
   .Zip プロジェクト ファイルを作成するビルド手順は次の例のようになります。  
  
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
  
## <a name="deploying-a-visual-studio-template"></a>Visual Studio テンプレートをデプロイします。  
 Visual Studio のテンプレートでは、パス情報は含まれません。 そのため、テンプレートの .zip ファイルは、Visual Studio に認識されている場所にデプロイする必要があります。 ProjectTemplates フォルダーの場所は、通常 **\<%localappdata% > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**します。  
  
 プロジェクト ファクトリをデプロイするには、インストール プログラムは、管理者特権が必要です。 Visual Studio のインストールのノードの下のテンプレートをデプロイします。 **...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates**します。  
  
## <a name="testing-a-visual-studio-template"></a>Visual Studio テンプレートのテスト  
 Visual Studio テンプレートを使用して、プロジェクト階層を作成し、かどうかをプロジェクト ファクトリをテストします。  
  
1. Visual Studio SDK 実験用インスタンスをリセットします。  
  
    [!INCLUDE[win7](../includes/win7-md.md)]: [スタート] メニューで、検索、 **Microsoft Visual Studio または Microsoft Visual Studio SDK/Tools**フォルダー、および選択 **、Microsoft Visual Studio 実験用インスタンスをリセット**。  
  
    以降のバージョンの Windows で: [スタート] 画面で、「 **Microsoft Visual Studio をリセット\<バージョン > 実験用インスタンス**します。  
  
2. コマンド プロンプト ウィンドウが表示されます。 単語が表示されたら`Press any key to continue`、enter キーを押します。 ウィンドウを閉じた後は、Visual Studio を開きます。  
  
3. SimpleProject プロジェクトをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
4. 実験用インスタンスの SimpleProject プロジェクトを作成します。 **新しいプロジェクト**ダイアログ ボックスで、 **SimpleProject**します。  
  
5. SimpleProject の新しいインスタンスを表示する必要があります。  
  
   ![](../extensibility/media/simpproj2-newproj.png "SimpProj2_NewProj")  
  
   ![](../extensibility/media/simpproj2-myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>プロジェクトの種類の子ノードを作成します。  
 プロジェクトの種類のノードに子ノードを追加することができます、**新しいプロジェクト** ダイアログ ボックス。  たとえば、SimpleProject プロジェクトの種類のコンソール アプリケーション、ウィンドウのアプリケーション、web アプリケーション、およびなどの子ノードがある可能性があります。  
  
 子ノード、プロジェクト ファイルを変更および追加で作成されます\<OutputSubPath > の子、 \<ZipProject > 要素。 ビルドまたは配置中に、テンプレートがコピーされると、すべての子ノードは、プロジェクト テンプレート フォルダーのサブフォルダーになります。  
  
 このセクションでは、SimpleProject プロジェクトの種類のコンソールの子ノードを作成する方法を示します。  
  
1.  \Templates\Projects\SimpleProject\ フォルダーの名前を \Templates\Projects\ConsoleApp\\します。  
  
2.  **プロパティ**ウィンドウは \Templates\Projects\ConsoleApp\ フォルダーで 5 つのすべてのファイルを選択し、確認、**ビルド アクション**に設定されている**ZipProject**します。  
  
3.  SimpleProject.vstemplate ファイルの末尾に次の行を追加、 \<TemplateData > 終了タグの直前のセクション。  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     これにより、コンソール アプリケーション テンプレートをコンソールの子ノードと子ノードの 1 つである SimpleProject 親ノードの両方を表示します。  
  
4.  SimpleProject.vstemplate ファイルを保存します。  
  
5.  .Csproj ファイルで、追加\<OutputSubPath > ZipProject 要素のそれぞれにします。 以前のように、プロジェクトをアンロードし、プロジェクト ファイルを編集します。  
  
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
  
## <a name="testing-the-project-type-child-node"></a>プロジェクトの種類の子ノードのテスト  
 変更されたプロジェクト ファイルをテストするかどうか、**コンソール**子ノードに表示されます、**新しいプロジェクト** ダイアログ ボックス。  
  
1. 実行、 **Microsoft Visual Studio の実験用インスタンスをリセット**ツール。  
  
2. SimpleProject プロジェクトをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
3. **新しいプロジェクト**ダイアログ ボックスで、をクリックして、 **SimpleProject**ノード。 **コンソール アプリケーション**テンプレートを表示する必要があります、**テンプレート**ウィンドウ。  
  
4. 展開、 **SimpleProject**ノード。 **コンソール**子ノードが表示されます。 **SimpleProject アプリケーション**テンプレートに引き続き表示されます、**テンプレート**ウィンドウ。  
  
5. . クリックして**キャンセル**およびデバッグの停止  
  
   ![](../extensibility/media/simpproj2-rollup.png "SimpProj2_Rollup")  
  
   ![](../extensibility/media/simpproj2-subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>プロジェクト テンプレートのパラメーターの置換  
 [基本的なプロジェクト システムでは、第 1 部作成](../extensibility/creating-a-basic-project-system-part-1.md)を上書きする方法を示しました、`ProjectNode.AddFileFromTemplate`メソッドをテンプレート パラメーター置換の基本的な種類の操作を行います。 このセクションより高度な Visual Studio テンプレートのパラメーターを使用する方法を説明します。  
  
 Visual Studio テンプレートを使用してプロジェクトを作成するときに、**新しいプロジェクト**ダイアログ ボックスで、プロジェクトをカスタマイズする文字列のテンプレートとパラメーターが置き換えられます。 テンプレート パラメーターは、始まり $time$ など、ドル記号で終了する特別なトークンです。 次の 2 つのパラメーターは、テンプレートに基づいてプロジェクトでカスタマイズを有効にするために特に便利です。  
  
- 1 ~ 10 $GUID$ は、新しい Guid に置き換えられます。 最大 10 個の一意な Guid guid1 $$ などを指定することができます。  
  
- $safeprojectname$ がユーザーによって指定された名前、**新しいプロジェクト** ダイアログ ボックスで、すべての安全でない文字とスペースを削除するように変更します。  
  
  テンプレート パラメーターの完全な一覧については、「[テンプレート パラメーター](../ide/template-parameters.md)」をご覧ください。  独自のカスタム テンプレート パラメーターを作成する場合を参照してください。 [NIB: 方法: カスタムのパラメーターをテンプレートに渡す](http://msdn.microsoft.com/en-us/5bc2ad11-84c7-4683-a276-e5e00d85d8fb)します。  
  
#### <a name="to-substitute-project-template-parameters"></a>プロジェクト テンプレートのパラメーター値  
  
1.  SimpleProjectNode.cs ファイルでは、削除、`AddFileFromTemplate`メソッド。  
  
2.  \Templates\Projects\ConsoleApp\SimpleProject.myproj ファイルで、 \<RootNamespace > プロパティ $safeprojectname$ にその値を変更します。  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  \Templates\Projects\SimpleProject\Program.cs ファイルで、ファイルの内容を次のコードに置き換えます。  
  
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
  
6.  新しく作成されたプロジェクトで Program.cs を開きます。 次のように表示されます (、ファイルの GUID 値は異なります。)。  
  
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
 種類のプロジェクト プロパティ ページを作成するには、ユーザーを表示し、テンプレートに基づくプロジェクトのプロパティを変更することができます。 このセクションでは、構成に依存しないプロパティ ページを作成する方法を示します。 この基本的なプロパティ ページでは、プロパティ グリッドを使用して、プロパティ ページ クラスで公開されるパブリック プロパティを表示します。  
  
 プロパティ ページ クラスを派生、`SettingsPage`基本クラス。 によって提供されるプロパティ グリッド、`SettingsPage`クラスはほとんどのプリミティブ データ型を認識し、それらを表示する方法を認識します。  さらに、`SettingsPage`クラスは、プロジェクト ファイルにプロパティ値を保持する方法を認識します。  
  
 このセクションで作成するプロパティ ページでは、alter、およびこれらのプロジェクト プロパティを保存できます。  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace します。  
  
1. SimpleProjectPackage.cs ファイルでこれを追加`ProvideObject`属性を`SimpleProjectPackage`クラス。  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    これは、プロパティ ページ クラスを登録します`GeneralPropertyPage`com。  
  
2. SimpleProjectNode.cs ファイル内にこれら 2 つのオーバーライドされたメソッドを追加、`SimpleProjectNode`クラス。  
  
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
  
    これら両方のメソッドは、プロパティ ページ Guid の配列を返します。  GeneralPropertyPage GUID は、配列内の唯一の要素、**プロパティ ページ** ダイアログ ボックスが 1 つだけのページに表示されます。  
  
3. SimpleProject プロジェクトに GeneralPropertyPage.cs をという名前のクラス ファイルを追加します。  
  
4. 次のコードを使用してこのファイルの内容に置き換えます。  
  
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
  
    `GeneralPropertyPage`クラスは、AssemblyName、OutputType、および RootNamespace は、次の 3 つのパブリック プロパティを公開します。 AssemblyName に set メソッドがあるないために、読み取り専用プロパティとして表示されます。 OutputType は列挙型の定数は、ドロップダウン リストとして表示されます。  
  
    `SettingsPage`基底クラスを提供します`ProjectMgr`プロパティを保持します。 `BindProperties`メソッドは`ProjectMgr`を永続化されたプロパティの値を取得し、対応するプロパティを設定します。  `ApplyChanges`メソッドは`ProjectMgr`プロパティの値を取得し、プロジェクト ファイルに保存します。 プロパティ設定メソッドのセット`IsDirty`プロパティを永続化する必要があることを指定する場合は true にします。  永続化は、プロジェクトまたはソリューションを保存するときに発生します。  
  
5. SimpleProject ソリューションをリビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
6. 実験用のインスタンスでは、新しい SimpleProject アプリケーションを作成します。  
  
7. Visual Studio では、Visual Studio テンプレートを使用してプロジェクトを作成する、プロジェクト ファクトリを呼び出します。 新しい Program.cs ファイルがコード エディターで開きます。  
  
8. プロジェクト ノードを右クリックして**ソリューション エクスプ ローラー**、 をクリックし、**プロパティ**します。 **[プロパティ ページ]** ダイアログ ボックスが表示されます。  
  
   ![](../extensibility/media/simpproj2-proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>テスト プロジェクトのプロパティ ページ  
 ここで変更してプロパティ値を変更するかどうかをテストできます。  
  
1. **MyConsoleApplication プロパティ ページ** ダイアログ ボックスで、変更、 **DefaultNamespace**に**MyApplication**します。  
  
2. 選択、 **OutputType**プロパティ、および選択**クラス ライブラリ**します。  
  
3. クリックして**適用**、順にクリックします**OK**します。  
  
4. 再度、**プロパティ ページ** ダイアログ ボックスし、変更が保存されていることを確認します。  
  
5. Visual Studio の実験用インスタンスを終了します。  
  
6. 実験用インスタンスをもう一度開きます。  
  
7. 再度、**プロパティ ページ** ダイアログ ボックスし、変更が保存されていることを確認します。  
  
8. Visual Studio の実験用インスタンスを終了します。  
  
   ![](../extensibility/media/simpproj2-proppage2.png "SimpProj2_PropPage2")

