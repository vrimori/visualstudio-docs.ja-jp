---
title: "チュートリアル: MSBuild プロジェクト ファイルのゼロからの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, チュートリアル"
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# チュートリアル: MSBuild プロジェクト ファイルのゼロからの作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

.NET Framework を対象とするプログラミング言語は、MSBuild プロジェクト ファイルを使用してアプリケーションのビルド プロセスを記述および制御します。 Visual Studio を使用して MSBuild プロジェクト ファイルを作成すると、適切な XML が自動的に追加されますが、 その XML がどのように構成されているかや、それに変更を加えてビルドを制御するにはどうすればよいかを知っておくことも有用です。  
  
 C++ プロジェクト用のプロジェクト ファイルを作成する方法の詳細については、次を参照してください。 [MSBuild (Visual c)](/visual-cpp/build/msbuild-visual-cpp)します。  
  
 このチュートリアルでは、テキスト エディターのみを使用して、基本的なプロジェクト ファイルをインクリメント方式で作成する方法について説明します。 このチュートリアルの手順を以下に示します。  
  
-   最低限の内容のみを含むアプリケーション ソース ファイルを作成します。  
  
-   最低限の内容のみを含む MSBuild プロジェクト ファイルを作成します。  
  
-   MSBuild が含まれるように PATH 環境変数を拡張します。  
  
-   プロジェクト ファイルを使用してアプリケーションをビルドします。  
  
-   ビルドを制御するためのプロパティを追加します。  
  
-   プロパティの値を変更してビルドを制御します。  
  
-   ビルド ターゲットを追加します。  
  
-   ターゲットを指定してビルドを制御します。  
  
-   インクリメンタル ビルドを実行します。  
  
 このチュートリアルでは、コマンド プロンプトでプロジェクトをビルドして結果を確認する方法を説明します。 MSBuild およびコマンド プロンプトで MSBuild を実行する方法の詳細については、次を参照してください。 [チュートリアル: MSBuild を使用して](../msbuild/walkthrough-using-msbuild.md)します。  
  
 このチュートリアルを実行するには、.NET Framework (Version 2.0、3.5、4.0、または 4.5) がインストールされている必要があります。これらには、このチュートリアルに必要な MSBuild と Visual C# コンパイラが含まれています。  
  
## <a name="creating-a-minimal-application"></a>最低限の内容のみを含むアプリケーションを作成する  
 ここでは、最低限の内容のみを含む Visual C# アプリケーション ソース ファイルをテキスト エディターで作成する方法を説明します。  
  
#### <a name="to-create-the-minimal-application"></a>最低限の内容のみを含むアプリケーションを作成するには  
  
1.  コマンド プロンプトで、アプリケーションを作成するフォルダーを \My Documents\ または参照 \Desktop\\します。  
  
2.  型 **md HelloWorld** \HelloWorld という名前のサブフォルダーを作成する\\です。  
  
3.  型 **cd HelloWorld** 新しいフォルダーに移動します。  
  
4.  メモ帳またはその他のテキスト エディターを起動して、次のコードを入力します。  
  
    ```  
    using System;  
  
    class HelloWorld  
    {  
        static void Main()  
        {  
    #if DebugConfig  
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");  
    #endif  
  
            Console.WriteLine("Hello, world!");  
        }  
    }  
    ```  
  
5.  このソース コード ファイルを Helloworld.cs という名前で保存します。  
  
6.  」と入力して、アプリケーションをビルド **csc helloworld.cs** コマンド プロンプト。  
  
7.  アプリケーションをテストする」と入力して **helloworld** コマンド プロンプト。  
  
      **こんにちは, world!** メッセージが表示されます。  
  
8.  」と入力して、アプリケーションを削除 **del helloworld.exe** コマンド プロンプト。  
  
## <a name="creating-a-minimal-msbuild-project-file"></a>最低限の内容のみを含む MSBuild プロジェクト ファイルを作成する  
 最低限の内容のみを含むアプリケーション ソース ファイルを作成できたので、次に、そのアプリケーションをビルドするための最低限の内容のみを含むプロジェクト ファイルを作成します。 このプロジェクト ファイルに含まれる要素は次のとおりです。  
  
-   必須のルート `Project` ノード  
  
-   項目要素を格納する `ItemGroup` ノード  
  
-   アプリケーション ソース ファイルを参照する項目要素  
  
-   アプリケーションをビルドするために必要なタスクを格納する `Target` ノード  
  
-   アプリケーションをビルドするために Visual C# コンパイラを起動する `Task` 要素  
  
#### <a name="to-create-a-minimal-msbuild-project-file"></a>最低限の内容のみを含む MSBuild プロジェクト ファイルを作成するには  
  
1.  テキスト エディターで、既存のテキストを次の 2 つの行に置き換えます。  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  次の `ItemGroup` ノードを `Project` ノードの子要素として挿入します。  
  
    ```  
    <ItemGroup>  
      <Compile Include="helloworld.cs" />  
    </ItemGroup>  
    ```  
  
     この `ItemGroup` には既に項目要素が含まれています。  
  
3.  `Target` ノードの子要素として `Project` ノードを追加します。 ノードの名前 `Build`します。  
  
    ```  
    <Target Name="Build">  
    </Target>  
    ```  
  
4.  次のタスク要素を `Target` ノードの子要素として挿入します。  
  
    ```  
    <Csc Sources="@(Compile)"/>  
    ```  
  
5.  このプロジェクト ファイルを Helloworld.csproj という名前で保存します。  
  
 最低限の内容のみを含むプロジェクト ファイルが完成すると、コードが次のようになります。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <Csc Sources="@(Compile)"/>    
  </Target>  
</Project>  
```  
  
 Build ターゲットのタスクは順番に実行されます。 ここでは、Visual C# コンパイラの `Csc` タスクが唯一のタスクです。 このタスクは、コンパイルするソース ファイルのリストを受け取ります。これは、`Compile` 項目の値によって渡されます。 `Compile` 項目は、Helloworld.cs という 1 つのソース ファイルのみを参照しています。  
  
> [!NOTE]
>  項目要素でワイルドカード文字のアスタリスク (*) を使用して、拡張子 .cs を持つすべてのファイルを参照することもできます。次に例を示します。  
>   
>  `<Compile Include="*.cs" />`  
>   
>  ただし、ワイルドカード文字を使用すると、ソース ファイルを追加または削除した場合にデバッグやターゲットの選択が困難になるため、できるだけ使用しないようにしてください。  
  
## <a name="extending-the-path-to-include-msbuild"></a>MSBuild が含まれるようにパスを拡張する  
 MSBuild を使用するには、.NET Framework フォルダーが含まれるように PATH 環境変数を拡張する必要があります。  
  
#### <a name="to-add-msbuild-to-your-path"></a>MSBuild をパスに追加するには  
  
-   Visual Studio 2013 では、MSBuild フォルダー (32 ビット オペレーティング システムの場合は `%ProgramFiles%\MSBuild`、64 ビット オペレーティング システムの場合は `%ProgramFiles(x86)%\MSBuild`) 内に MSBuild.exe があります。  
  
     コマンド プロンプトで次のように入力します。 **設定 PATH=%PATH%;%ProgramFiles%\MSBuild** または **パスを設定する = %path%; % %programfiles% (x86) %\MSBuild**します。  
  
     または、Visual Studio をインストールした場合を使えば、 **Visual Studio コマンド プロンプト**, 、MSBuild フォルダーへのパスします。  
  
## <a name="using-the-project-file-to-build-the-application"></a>プロジェクト ファイルを使用してアプリケーションをビルドする  
 次に、先ほど作成したプロジェクト ファイルを使用してアプリケーションをビルドします。  
  
#### <a name="to-build-the-application"></a>アプリケーションをビルドするには  
  
1.  コマンド プロンプトで「 **msbuild helloworld.csproj/t:Build**します。  
  
     Visual C# コンパイラが呼び出され、Helloworld プロジェクト ファイルの Build ターゲットがビルドされて、Helloworld アプリケーションが作成されます。  
  
2.  アプリケーションをテストする」と入力して **helloworld**します。  
  
      **こんにちは, world!** メッセージが表示されます。  
  
> [!NOTE]
>  詳細レベルを上げると、ビルドの詳細情報を表示できます。 詳細レベルを "detailed" に設定するには、コマンド プロンプトで次のいずれかのコマンドを入力します。  
>   
>  **msbuild helloworld.csproj/t:Build/verbosity: 詳細**  
  
## <a name="adding-build-properties"></a>ビルド プロパティを追加する  
 プロジェクト ファイルにビルド プロパティを追加すると、ビルドをさらに細かく制御できます。 ここでは、次のプロパティを追加します。  
  
-   アプリケーションの名前を指定する `AssemblyName` プロパティ  
  
-   アプリケーションを格納するフォルダーを指定する `OutputPath` プロパティ  
  
#### <a name="to-add-build-properties"></a>ビルド プロパティを追加するには  
  
1.  」と入力して、既存のアプリケーションを削除 **del helloworld.exe** コマンド プロンプト。  
  
2.  プロジェクト ファイルで、次の `PropertyGroup` 要素を開始 `Project` 要素の直後に挿入します。  
  
    ```  
    <PropertyGroup>  
      <AssemblyName>MSBuildSample</AssemblyName>  
      <OutputPath>Bin\</OutputPath>  
    </PropertyGroup>  
    ```  
  
3.  次のタスクを Build ターゲットの `Csc` タスクの直前に追加します。  
  
    ```  
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />  
    ```  
  
     この `MakeDir` タスクは、`OutputPath` プロパティによって指定されるフォルダーを、同名のフォルダーが存在しない場合に作成します。  
  
4.  次の `OutputAssembly` 属性を `Csc` タスクに追加します。  
  
    ```  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    ```  
  
     この属性は、Visual C# コンパイラに対して、`AssemblyName` プロパティによって指定されるアセンブリを生成し、`OutputPath` プロパティによって指定されるフォルダーに配置するように指定します。  
  
5.  変更内容を保存します。  
  
 プロジェクト ファイルのコードが次のようになります。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
</Project>  
```  
  
> [!NOTE]
>  バック スラッシュを追加することをお勧め (\\) で指定するときに、フォルダー名の末尾にパスの区切り記号、 `OutputPath` 要素に追加するのではなく、 `OutputAssembly` の属性、 `Csc` タスクです。 次に例を示します。  
>   
>  `<OutputPath>Bin\</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`  
>   
>  この形式が次の形式より推奨されます。  
>   
>  `<OutputPath>Bin</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`  
  
## <a name="testing-the-build-properties"></a>ビルド プロパティをテストする  
 次に、ビルド プロパティで出力フォルダーとアプリケーション名を指定したプロジェクト ファイルを使用してアプリケーションをビルドします。  
  
#### <a name="to-test-the-build-properties"></a>ビルド プロパティをテストするには  
  
1.  コマンド プロンプトで「 **msbuild helloworld.csproj/t:Build**します。  
  
     \Bin\ フォルダーが作成され、Visual C# コンパイラが呼び出されて、MSBuildSample アプリケーションが作成されて \Bin\ フォルダーに配置されます。  
  
2.  \Bin\ フォルダーが作成されたことと、そこに MSBuildSample アプリケーションが含まれていることを確認するには、入力 **dir Bin**します。  
  
3.  アプリケーションをテストする」と入力して **bin \msbuildsample**します。  
  
      **こんにちは, world!** メッセージが表示されます。  
  
## <a name="adding-build-targets"></a>ビルド ターゲットを追加する  
 次に、次の 2 つのターゲットをプロジェクト ファイルに追加します。  
  
-   古いファイルを削除する Clean ターゲット  
  
-   `DependsOnTargets` 属性を使用して Build タスクの前に強制的に Clean タスクを実行する Rebuild ターゲット  
  
 ターゲットが複数になるので、Build ターゲットを既定のターゲットに設定します。  
  
#### <a name="to-add-build-targets"></a>ビルド ターゲットを追加するには  
  
1.  プロジェクト ファイルで、Build ターゲットの直後に次の 2 つのターゲットを追加します。  
  
    ```  
    <Target Name="Clean" >  
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
    ```  
  
     Clean ターゲットは、Delete タスクを呼び出してアプリケーションを削除します。 Rebuild ターゲットは、Clean ターゲットと Build ターゲットの両方が実行されるまで実行されません。 Rebuild ターゲットにはタスクは含まれていませんが、このターゲットにより、Build ターゲットの前に Clean ターゲットが実行されるようになります。  
  
2.  次の `DefaultTargets` 属性を開始 `Project` 要素に追加します。  
  
    ```  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ```  
  
     これにより、Build ターゲットが既定のターゲットに設定されます。  
  
 プロジェクト ファイルのコードが次のようになります。  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
  <Target Name="Clean" >  
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
</Project>  
```  
  
## <a name="testing-the-build-targets"></a>ビルド ターゲットをテストする  
 新しいビルド ターゲットを使用して、プロジェクト ファイルの以下の機能をテストします。  
  
-   既定のビルドをビルドする。  
  
-   コマンド プロンプトでアプリケーション名を設定する。  
  
-   別のアプリケーションをビルドする前にアプリケーションを削除する。  
  
-   別のアプリケーションをビルドせずにアプリケーションを削除する。  
  
#### <a name="to-test-the-build-targets"></a>ビルド ターゲットをテストするには  
  
1.  コマンド プロンプトで「 **msbuild helloworld.csproj/p:AssemblyName = Greetings**します。  
  
     使用していないため、 **/t** ターゲットを明示的に設定に切り替えると、MSBuild は、既定の Build ターゲットを実行します。  **/P** のオーバーライドを切り替えて、 `AssemblyName` プロパティ、新しい値と `Greetings`です。 これにより、Greetings.exe という新しいアプリケーションが \Bin\ フォルダーに作成されます。  
  
2.  \Bin\ フォルダーに MSBuildSample アプリケーションと新しい Greetings アプリケーションの両方が含まれていることを確認するには、次のように入力します。 **dir Bin**します。  
  
3.  」と入力して、Greetings アプリケーションをテスト **bin \greetings**します。  
  
      **こんにちは, world!** メッセージが表示されます。  
  
4.  」と入力して、MSBuildSample アプリケーションを削除 **msbuild helloworld.csproj/t: クリーン**します。  
  
     既定値を持つアプリケーションを削除する Clean タスクが実行されて `AssemblyName` プロパティの値、 `MSBuildSample`です。  
  
5.  」と入力して、Greetings アプリケーションを削除 **msbuild helloworld.csproj/t:/p:AssemblyName のクリーンアップのあいさつを =**です。  
  
     持つアプリケーションを削除する Clean タスクが実行されて、指定された **AssemblyName** プロパティの値、 `Greetings`です。  
  
6.  \Bin\ フォルダーが空になったことを確認するには、入力 **dir Bin**します。  
  
7.  型 **msbuild**します。  
  
     プロジェクト ファイルが指定されていませんが、現在のフォルダーにはプロジェクト ファイルが 1 つしかないため、helloworld.csproj ファイルがビルドされます。 その結果、\Bin\ フォルダーに MSBuildSample アプリケーションが作成されます。  
  
     \Bin\ フォルダーに MSBuildSample アプリケーションが含まれていることを確認するには、次のように入力します。 **dir Bin**します。  
  
## <a name="building-incrementally"></a>インクリメンタル ビルドを実行する  
 MSBuild では、ターゲットが依存しているソース ファイルやターゲット ファイルが変更された場合にのみターゲットをビルドすることができます。 ファイルが変更されているかどうかはファイルのタイム スタンプを使用して特定されます。  
  
#### <a name="to-build-incrementally"></a>インクリメンタル ビルドを実行するには  
  
1.  プロジェクト ファイルで、開始 Build ターゲットに次の属性を追加します。  
  
    ```  
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"  
    ```  
  
     ここでは、`Compile` 項目グループに指定されている入力ファイルに Build ターゲットが依存していること、出力対象がアプリケーション ファイルであることを指定しています。  
  
     この結果、Build ターゲットのコードは次のようになります。  
  
    ```  
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">  
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    ```  
  
2.  」と入力して、ビルド ターゲットをテスト **msbuild/v:d** コマンド プロンプト。  
  
     helloworld.csproj が既定のプロジェクト ファイルであること、Build が既定のターゲットであることに注意してください。  
  
      **/V:d** ビルド処理の詳細な説明を指定します。  
  
     以下の行が表示されます。  
  
     **すべての出力ファイルが入力ファイルに対して最新の状態にあるために、Build ターゲットをスキップしています。**  
  
     **入力ファイル: HelloWorld.cs**  
  
     **出力ファイル: BinMSBuildSample.exe**  
  
     アプリケーションがビルドされてから変更されたソース ファイルがないため、Build ターゲットはスキップされます。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例は、[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] アプリケーションをコンパイルし、出力ファイル名を含むメッセージを記録するプロジェクト ファイルを示しています。  
  
### <a name="code"></a>コード  
  
```c#  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files of type CSFile -->  
        <CSC  
            Sources = "@(CSFile)"  
            OutputAssembly = "$(appname).exe">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
### <a name="comments"></a>コメント  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] アプリケーションをコンパイルし、出力ファイル名を含むメッセージを記録するプロジェクト ファイルを示しています。  
  
### <a name="code"></a>コード  
  
```vb#  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldVB</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <VBFile Include = "consolehwvb1.vb"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">      
        <!-- Run the Visual Basic compilation using input files of type VBFile -->  
        <VBC  
            Sources = "@(VBFile)"  
            OutputAssembly= "$(appname).exe">  
            <!-- Set the OutputAssembly attribute of the VBC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </VBC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="whats-next"></a>次の内容  
 このチュートリアルで説明した作業の大半は、Visual Studio で自動的に実行できます。 Visual Studio を使用して、作成、編集、ビルド、および MSBuild プロジェクト ファイルをテストする方法については、次を参照してください。 [チュートリアル: MSBuild を使用して](../msbuild/walkthrough-using-msbuild.md)します。  
  
## <a name="see-also"></a>関連項目  
[MSBuild の概要](../msbuild/msbuild1.md)  
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)