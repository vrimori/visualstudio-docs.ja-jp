---
title: 配置後の問題の診断 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
caps.latest.revision: 66
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6c4c60265fda66f7506fe6d886fa671527c1587
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785457"
---
# <a name="diagnose-problems-after-deployment"></a>配置後の問題の診断
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliTrace を使用して、ASP.NET Web アプリの配置後に問題を診断するには、リリースについてのビルド情報を含めます。こうすることで、Visual Studio が、IntelliTrace ログをデバッグするために必要な正しいソース ファイルとシンボル ファイルを自動的に検索できるようになります。  
  
 また、Microsoft Monitoring Agent を使用して IntelliTrace を制御している場合は、Web サーバー上でアプリケーション パフォーマンスの監視をセットアップする必要もあります。 これにより、アプリがイベントを実行して IntelliTrace ログ ファイルに保存する間に、診断イベントが記録されます。 次に Visual Studio Enterprise (ただし、Professional および Community Edition を除く) でイベントを確認し、イベントが発生したコードに移動できます。さらに、その時点で記録された値を確認し、実行されたコード内を前後に移動できます。 問題を見つけて解決したら、リリースをビルド、リリース、および監視するサイクルを繰り返して、将来発生する可能性がある問題をさらに早い段階で速やかに解決できます。  
  
 ![コード、ビルド、リリース、監視、診断、修正](../debugger/media/ffr-cycle.png "FFR_Cycle")  
  
 **必要があります。**  
  
-   ビルドを設定するための Visual Studio 2015 または Team Foundation Server 2015、2013、2012、2010  
  
-   アプリを監視して診断データを記録するための Microsoft Monitoring Agent  
  
-   診断データを確認して IntelliTrace でコードをデバッグするための Visual Studio Enterprise (ただし、Professional および Community Edition を除く)  
  
##  <a name="SetUpBuild"></a> 手順 1: 含めるビルドをリリース情報  
 ビルド プロセスを設定して Web プロジェクトのビルド マニフェスト (BuildInfo.config ファイル) を作成し、このマニフェストをリリースに含めます。 このマニフェストには、特定のビルドを作成するために使用されたプロジェクト、ソース管理、およびビルド システムに関する情報が含まれます。 この情報は、IntelliTrace ログを開いて記録されたイベントを確認した後に、Visual Studio が対応するソースとシンボルを見つけるのに役立ちます。  
  
###  <a name="AutomatedBuild"></a> Team Foundation Server を使用して自動化されたビルドのビルド マニフェストを作成します。  
 Team Foundation バージョン管理と Git のいずれを使用するにしても、これらの手順に従います。  
  
####  <a name="TFS2013"></a> Team Foundation Server 2013  
 ビルド定義を設定して、ソース、ビルド、およびシンボルの場所をビルド マニフェスト (BuildInfo.config ファイル) に追加します。 Team Foundation ビルドは自動的にこのファイルを作成し、そのファイルをプロジェクトの出力フォルダーに配置します。  
  
1. [ビルド定義を編集するか、新しいビルド定義を作成します。](http://msdn.microsoft.com/library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)  
  
    ![ビルド定義を TFS 2013 での表示](../debugger/media/ffr-tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")  
  
2. 既定のテンプレート (TfvcTemplate.12.xaml) または独自のカスタム テンプレートを選択します。  
  
    ![ビルド プロセス テンプレートの選択&#45;TFS 2013](../debugger/media/ffr-tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  
  
3. ソースのインデックスが自動的に作成されるように、シンボル (PDB) ファイルの保存場所を指定します。  
  
    カスタム テンプレートを使用する場合は、ソースにインデックスを付けるアクティビティがカスタム テンプレートに含まれていることを確認します。 後の手順で、MSBuild 引数を追加して、シンボル ファイルの保存場所を指定できます。  
  
    ![ビルド定義の TFS 2013 でのシンボル パスを設定](../debugger/media/ffr-tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  
  
    シンボルの詳細については、「 [シンボル データを発行する](http://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6)」を参照してください。  
  
4. この MSBuild 引数を追加して、TFS とシンボルの場所をビルド マニフェスト ファイルに含めます。  
  
    **/p:IncludeServerNameInBuildInfo = true**  
  
    Web サーバーにアクセスできるすべてのユーザーが、ビルド マニフェスト内のこれらの場所を確認できます。 ソース サーバーがセキュリティで保護されていることを確認してください。  
  
5. カスタム テンプレートを使用する場合は、この MSBuild 引数を追加して、シンボル ファイルを保存する場所を指定します。  
  
    **/p:BuildSymbolStorePath =**\<*シンボルへのパス*>  
  
    ![ビルド定義の TFS 2013 ビルド サーバーの情報を含める](../debugger/media/ffr-tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")  
  
    以下の行を Web プロジェクト ファイル (.csproj または .vbproj) に追加します。  
  
   ```  
   <!-- Import the targets file. Change the folder location as necessary. -->  
      <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />  
  
   ```  
  
6. 新しいビルドを実行します。  
  
   **手順 2:** [手順 2: Release your app](#DeployRelease)  
  
####  <a name="TFS2012_2010"></a> Team Foundation Server 2012 または 2010  
 プロジェクトのビルド マニフェスト (BuildInfo.config ファイル) を自動的に作成し、プロジェクトの出力フォルダーに配置するには、次の手順を実行します。 このファイルは出力フォルダーで "*ProjectName*.BuildInfo.config" と表示されますが、アプリの発行後に配置フォルダーで "BuildInfo.config" という名前に変更されます。  
  
1. Team Foundation ビルド サーバーに、Visual Studio 2013 (任意のエディション) をインストールします。  
  
2. ビルド定義で、シンボル保存場所を指定します。その結果、ソースのインデックスが自動的に作成されます。  
  
    カスタム テンプレートを使用する場合は、ソースにインデックスを付けるアクティビティがカスタム テンプレートに含まれていることを確認します。  
  
3. 次の MSBuild 引数を、ビルド定義に追加します。  
  
   -   **/p:VisualStudioVersion 12.0 を =**  
  
   -   **/p:MSBuildAssemblyVersion 12.0 を =**  
  
   -   **/tv:12.0**  
  
   -   **/p:IncludeServerNameInBuildInfo = true**  
  
   -   **/p:BuildSymbolStorePath =**\<*シンボルへのパス*>  
  
4. 新しいビルドを実行します。  
  
   **手順 2:** [手順 2: Release your app](#DeployRelease)  
  
###  <a name="ManualBuild"></a> Visual Studio を使用して手動ビルドのビルド マニフェストを作成します。  
 プロジェクトのビルド マニフェスト (BuildInfo.config ファイル) を自動的に作成し、プロジェクトの出力フォルダーに配置するには、次の手順を実行します。 このファイルは出力フォルダーで "*ProjectName*.BuildInfo.config" と表示されますが、アプリの発行後に配置フォルダーで "BuildInfo.config" という名前に変更されます。  
  
1. **[ソリューション エクスプローラー]** で、Web プロジェクトをアンロードします。  
  
2. プロジェクト ファイル (.csproj、.vbproj) を開きます。 次の行を追加します。  
  
   ```xml  
   <!-- **************************************************** -->  
   <!-- Build info -->  
   <PropertyGroup>  
      <!-- Generate the BuildInfo.config file -->  
      <GenerateBuildInfoConfigFile>True</GenerateBuildInfoConfigFile>  
      <!-- Include server name in build info -->   
      <IncludeServerNameInBuildInfo>True</IncludeServerNameInBuildInfo>   
      <!-- Include the symbols path so Visual Studio can find the matching deployed code when you start debugging. -->  
      <BuildSymbolStorePath><path to symbols></BuildSymbolStorePath>  
   </PropertyGroup>  
   <!-- **************************************************** -->  
   ```  
  
3. 更新されたプロジェクト ファイルをチェックインします。  
  
4. 新しいビルドを実行します。  
  
   **手順 2:** [手順 2: Release your app](#DeployRelease)  
  
###  <a name="MSBuild"></a> MSBuild.exe を使用して手動ビルドのビルド マニフェストを作成します。  
 ビルドの実行時に次のビルド引数を追加します。  
  
 **/p:GenerateBuildInfoConfigFile = true**  
  
 **/p:IncludeServerNameInBuildInfo = true**  
  
 **/p:BuildSymbolStorePath =**\<*シンボルへのパス*>  
  
##  <a name="DeployRelease"></a> 手順 2: アプリをリリースします。  
 アプリを配置するためのビルド プロセスにより作成された [Web.Deploy パッケージ](http://msdn.microsoft.com/library/dd394698.aspx) を使用する場合、ビルド マニフェストの名前は "*ProjectName*.BuildInfo.config" から "BuildInfo.config" へ自動的に変更され、Web サーバー上にあるアプリの Web.config ファイルと同じフォルダーに配置されます。  
  
 他の方法を使用してアプリを配置する場合は、ビルド マニフェストの名前が "*ProjectName*.BuildInfo.config" から "BuildInfo.config" へ変更され、Web サーバー上にあるアプリの Web.config ファイルと同じフォルダーに配置されていることを確認します。  
  
## <a name="step-3-monitor-your-app"></a>手順 3: アプリを監視する  
 Web サーバー上でアプリケーション パフォーマンスの監視を設定して、アプリの問題の監視、診断イベントの記録、および IntelliTrace ログ ファイルへのイベントの保存ができるようにします。 「 [Monitor your release for deployment problems (配置の問題に関するリリースの監視)](../debugger/using-the-intellitrace-stand-alone-collector.md)」を参照してください。  
  
##  <a name="InvestigateEvents"></a> 手順 4: 問題を見つける  
 記録されたイベントを確認し、IntelliTrace を使用してコードをデバッグするには、開発用コンピューターまたは別のコンピューターに Visual Studio Enterprise がインストールされている必要があります。 問題の診断に役立つ CodeLens、デバッガー マップ、コード マップなどのツールを使用することもできます。  
  
### <a name="open-the-intellitrace-log-and-matching-solution"></a>IntelliTrace ログと対応するソリューションを開く  
  
1.  IntelliTrace ログ (.iTrace ファイル) を Visual Studio Enterprise から開きます。 同じコンピューターに Visual Studio Enterprise がある場合は、ファイルをダブルクリックするだけです。  
  
2.  **[ソリューションを開く]** を選ぶと、対応するソリューションまたはプロジェクトが自動的に開きます (そのプロジェクトがソリューションの一部として組み込まれていない場合)。 [Q: IntelliTrace ログには、配置したアプリに関する情報がありません。なぜこのようなことが起きたのですか。どうしたらよいですか。](#InvalidConfigFile)  
  
     Visual Studio では、対応するソリューションまたはプロジェクトが開くと、保留中のすべての変更が自動的にシェルブされます。 このシェルブセットの詳細情報を取得するには、 **[出力]** ウィンドウまたは **チーム エクスプローラー**を確認します。  
  
     変更する前に、適切なソースがあることを確認してください。 分岐を使用する場合、Visual Studio が対応するソースを検出した分岐 (リリース ブランチなど) とは異なる分岐で作業する可能性があります。  
  
     ![IntelliTrace ログからソリューションを開く](../debugger/media/ffr-itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")  
  
     このソリューションまたはプロジェクトに対するワークスペースを既に割り当てた場合は、Visual Studio によってそのワークスペースが選択され、検出されたソースが配置されます。  
  
     ![マップされたワークスペースには、ソース管理から開く](../debugger/media/ffr-openprojectfromsourcecontrol-mapped.png "FFR_OpenProjectFromSourceControl_Mapped")  
  
     それ以外の場合は、別のワークスペースを選択するか、新しいワークスペースを作成します。 Visual Studio では、分岐全体がこのワークスペースに割り当てられます。  
  
     ![ソース管理から開く&#45;新しいワークスペースを作成する](../debugger/media/ffr-openprojectfromsourcecontrol-createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")  
  
     特定のマッピングを備えたワークスペースや、コンピューターとは名前が異なるワークスペースを作成するには、 **[管理]** を選択します。  
  
     [Q: Visual Studio は選択したワークスペースが対象となるをなぜように言ってするのでしょうか。](#IneligibleWorkspace)  
  
     [Q: チーム コレクションまたは別のコレクションを選択するまでを続行できないのはなぜでしょうか。](#ChooseTeamProject)  
  
### <a name="diagnose-a-performance-problem"></a>パフォーマンスの問題を診断する  
  
1.  **[パフォーマンス違反]** で、記録されたパフォーマンス イベント、総実行時間、およびその他のイベント情報を確認します。 その後、特定のパフォーマンス イベントの発生時に呼び出されたメソッドをさらに掘り下げます。  
  
     ![パフォーマンス イベントの詳細表示](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     イベントをダブルクリックするだけでもかまいません。  
  
2.  イベント ページで、これらの呼び出しの実行時間を確認します。 実行ツリーで、時間がかかっている呼び出しを見つけます。  
  
     複数の呼び出しが入れ子などの形式で存在する場合は、最も低速な呼び出しが独自のセクションに表示されます。  
  
     その呼び出しを展開して、その時点で記録された、入れ子になったすべての呼び出しと値を確認します。 その後、その呼び出しからデバッグを開始します。  
  
     ![メソッドの呼び出しからデバッグを開始](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     呼び出しをダブルクリックするだけでもかまいません。  
  
     アプリケーション コードにメソッドが含まれる場合、Visual Studio はそのメソッドに移動します。  
  
     ![パフォーマンス イベントからアプリケーション コードに移動して](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     これで、他の記録された値、つまり呼び出し履歴を確認したり、コードをステップ実行したりできます。また、 **IntelliTrace** ウィンドウを使用して、パフォーマンス イベントの発生時に呼び出された [その他のメソッド間を "時間内に" 前後に移動することもできます](../debugger/intellitrace.md) 。 [IntelliTrace ログ内の他のイベントと情報について](../debugger/using-saved-intellitrace-data.md)[What else can I do from here?](#WhatElse)[パフォーマンス イベントに関する詳細を確認しましょう。](http://blogs.msdn.com/b/visualstudioalm/archive/2013/09/20/performance-details-in-intellitrace.aspx)  
  
### <a name="diagnose-an-exception"></a>例外の診断  
  
1.  **[例外データ]** では、記録された例外イベントとその種類、メッセージ、およびその例外がいつ発生したかを確認できます。 コードをさらに掘り下げるには、例外グループの最新のイベントからデバッグを開始します。  
  
     ![例外イベントからデバッグを開始](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     イベントをダブルクリックするだけでもかまいません。  
  
     例外がアプリケーション コードで発生した場合、Visual Studio は例外が発生した場所に移動します。  
  
     ![例外イベントからアプリケーション コードに移動して](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     これで、他の記録された値、つまり呼び出し履歴を確認したり、 **IntelliTrace** ウィンドウを使用して、 [記録されたその他のイベント間を "時間内に" 前後に移動したりできます](../debugger/intellitrace.md)。また、関連するコードや、その時点で記録された値の間も前後に移動できます。 [他すべてのイベントと、IntelliTrace ログ内の情報とは](../debugger/using-saved-intellitrace-data.md)  
  
###  <a name="WhatElse"></a> ここからすれば他に何をしますか。  
  
-   [このコードのさらに詳細な情報を入手します](../ide/find-code-changes-and-other-history-with-codelens.md)。 エディターから離れずに、このコードの参照、変更履歴、関連するバグ、作業項目、コード レビュー、または単体テストを検索するには、エディターの CodeLens インジケーターを使用します。  
  
     ![CodeLens&#45;このコードへの参照を表示](../debugger/media/ffr-itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")  
  
     ![CodeLens&#45;変更このコードの履歴の表示](../debugger/media/ffr-itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")  
  
-   [デバッグ中に、コード内の位置をマップします。](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) デバッグ セッション中に呼び出されたメソッドを視覚的に追跡するには、呼び出し履歴を割り当てます。  
  
     ![デバッグ中に呼び出し履歴でマップ](../debugger/media/ffr-itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")  
  
###  <a name="FAQ"></a> Q & A  
  
####  <a name="WhyInclude"></a> Q: 自分のプロジェクト、ソース管理、ビルド、およびリリースを使用したシンボルに関する情報を含めますか。  
 Visual Studio はこの情報を使用して、デバッグしようとするリリースに対応するソリューションやソースを検索します。 IntelliTrace ログを開き、イベントを選択してデバッグを開始した後に、Visual Studio はシンボルを使用して検索を実行し、イベントが発生したコードを表示します。 それから、記録された値を確認し、実行中のコード内を前後に移動できます。  
  
 TFS を使用しており、この情報がビルド マニフェスト (BuildInfo.config ファイル) ではない場合、Visual Studio は対応するソースとシンボルを現在接続されている TFS 上で検索します。 Visual Studio が適切な TFS または対応するソースを見つけられない場合、他の TFS を選択するように求めるプロンプトが表示されます。  
  
####  <a name="InvalidConfigFile"></a> Q: IntelliTrace ログには、配置したアプリに関する情報がありません。 なぜこのようなことが起きたのですか。 どうしたらよいですか。  
 この問題は、開発用コンピューターから配置した場合や配置中に TFS に接続していない場合に発生する可能性があります。  
  
1.  プロジェクトの配置フォルダーに移動します。  
  
2.  ビルド マニフェスト (BuildInfo.config ファイル) を検索して開きます。  
  
3.  ファイル内に以下の必要な情報があることを確認します。  
  
- **ProjectName**  
  
   Visual Studio 内のプロジェクトの名前。 例えば:  
  
  ```  
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>  
  ```  
  
- **発生しました。 SourceControl**  
  
- ソース管理システムに関する情報と以下の必須プロパティ:  
  
  - **TFS**  
  
    - **ProjectCollectionUri**: Team Foundation Server およびプロジェクト コレクションの URI  
  
    - **ProjectItemSpec**: アプリのプロジェクト ファイル (.csproj または .vbproj) へのパス  
  
    - **ProjectVersionSpec**: プロジェクトのバージョン  
  
      例えば:  
  
    ```  
    <SourceControl type="TFS">  
       <TfsSourceControl>  
          <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>  
          <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>  
          <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>  
       </TfsSourceControl>  
    </SourceControl>  
    ```  
  
  - **Git**  
  
    - **GitSourceControl**: **GitSourceControl** スキーマの場所  
  
    - **RepositoryUrl**: Team Foundation Server、プロジェクト コレクション、および Git リポジトリの URI  
  
    - **ProjectPath**: アプリのプロジェクト ファイル (.csproj or .vbproj) へのパス  
  
    - **CommitId**: コミットの ID  
  
      例えば:  
  
    ```  
    <SourceControl type="Git">   
       <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">  
          <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>  
          <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>  
          <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>  
       </GitSourceControl>  
    </SourceControl>  
    ```  
  
- **ビルド**  
  
   ビルド システムに関する情報 ( `"TeamBuild"` または `"MSBuild"`) と以下の必須プロパティ:  
  
  - **BuildLabel** (TeamBuild の場合): ビルドの名前と番号。 このラベルは配置イベントの名前としても使用されます。 ビルド番号について詳しくは、「 [完了したビルドにわかりやすい名前を付けるためにビルド番号を使用](http://msdn.microsoft.com/library/1f302e9d-4b0a-40b5-8009-b69ca6f988c3)」をご覧ください。  
  
  - **SymbolPath** (推奨): セミコロンで区切ったシンボル (PDB ファイル) の場所に関する URI の一覧。 これらの URI は、URL または UNC のいずれかです。 これにより、Visual Studio は対応するシンボルを容易に検索でき、デバッグに役立ちます。  
  
  - **BuildReportUrl** (TeamBuild の場合): TFS でのビルド レポートの場所  
  
  - **BuildId** (TeamBuild の場合): TFS でのビルドの詳細の URI。 この URI は配置イベントの ID としても使用されます。 TeamBuild を使用していない場合は、この ID は一意である必要があります。  
  
  - **BuiltSolution**: 対応するソリューションを検索して開くために Visual Studio が使用するソリューション ファイルへのパス。 これは、 **SolutionPath** MsBuild プロパティの内容です。  
  
    例えば:  
  
  - **TFS**  
  
    ```  
    <Build type="TeamBuild">  
       <MsBuild>  
          <BuildLabel kind="label">FabrikamFiber_BuildAndPublish_20130813.1</BuildLabel>  
          <SymbolPath>\\fabrikamfiber\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuildReportUrl kind="informative, url" url="http://fabrikamfiber:8080/tfs/FabrikamFiber/_releasePipeline/FindRelease?buildUri=fabrikamfiber%3a%2f%2f%2fBuild%2fBuild%2f448">Build Report Url</BuildReportUrl>  
          <BuildId kind="id">1c4444d2-518d-4673-a590-dce2773c7744,fabrikamfiber:///Build/Build/448</BuildId>  
          <BuiltSolution>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MsBuild>  
    </Build>  
    ```  
  
  - **Git**  
  
    ```  
    <Build type="MSBuild">   
       <MSBuild>  
          <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MSBuild>  
    </Build>  
    ```  
  
####  <a name="IneligibleWorkspace"></a> Q: Visual Studio は選択したワークスペースが対象となるをなぜように言ってするのでしょうか。  
 **A:** 選択したワークスペースのソース コントロール フォルダーとローカル フォルダーの間にマッピングがありません。 このワークスペースのマッピングを作成するには、 **[管理]** を選択します。 それ以外の場合は、既に割り当てられているワークスペースを選択するか、新しいワークスペースを作成します。  
  
 ![マップされたワークスペースとソース管理から開く](../debugger/media/ffr-openprojectfromsourcecontrol-notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")  
  
####  <a name="ChooseTeamProject"></a> Q: チーム コレクションまたは別のコレクションを選択するまでを続行できないのはなぜでしょうか。  
 **A:** これは次の理由によって発生する場合があります。  
  
-   Visual Studio が TFS に接続されていない。  
  
     ![ソース管理から開く&#45;未接続](../debugger/media/ffr-openprojectfromsourcecontrol-notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")  
  
-   Visual Studio が、現在のチーム コレクションでソリューションまたはプロジェクトを見つけられなかった。  
  
     ビルド マニフェスト ファイル (\<*ProjectName*>。BuildInfo.config) が Visual Studio が対応するソースを検索する場所を指定していない Visual Studio では、現在接続されている TFS を使用して、、対応するソリューションまたはプロジェクトを検索します。 対応するソースが現在のチーム コレクションにない場合、Visual Studio は、別のチーム コレクションに接続するように求めるメッセージを表示します。  
  
-   Visual Studio ビルド マニフェスト ファイルで指定されたコレクションでソリューションまたはプロジェクトが見つかりませんでした (\<*ProjectName*>。BuildInfo.config)。  
  
     新しい TFS に移行したため、対応するソースが指定 TFS にない、あるいは TFS 自体が存在しない可能性があります。 指定された TFS が存在しない場合、Visual Studio は 約 1 分後にタイムアウトになり、別のコレクションに接続するように求めるメッセージが表示される可能性があります。 操作を続行するには、正しい TFS サーバーに接続します。  
  
     ![ソース管理から開く&#45;移行](../debugger/media/ffr-openprojectfromsourcecontrol-migrated.png "FFR_OpenProjectFromSourceControl_Migrated")  
  
####  <a name="WhatWorkspace"></a> Q: ワークスペースとは?  
 **A:** [ワークスペースにはソースのコピーが格納](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a) されるので、作業をチェックインする前に、そのコピーを別に開発およびテストできます。 検出されたソリューションまたはプロジェクトに特別に割り当てられたワークスペースがまだない場合、Visual Studio では、使用可能なワークスペースを選択するか、既定のワークスペースと同じコンピューター名で新しいワークスペースを作成するように求めるメッセージが表示されます。  
  
####  <a name="UntrustedSymbols"></a> 信頼されていないシンボルに関するメッセージを取得する q はありますか  
 ![信頼されていないシンボル パスでデバッグしますか。](../debugger/media/ffr-ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")  
  
 **A:** このメッセージを表示するときに、ビルド マニフェスト ファイルでシンボル パス (\<*ProjectName*>。BuildInfo.config) が、信頼されたシンボル パスの一覧に含まれていません。 このパスをシンボル パスの一覧に追加するには、デバッガー オプションを使用します。





