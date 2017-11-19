---
redirect_url: /visualstudio/extensibility/what-s-new-in-the-visual-studio-2017-sdk/
ms.openlocfilehash: 5706797ed88dce5b2f481b17d99e9501b960ddca
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
タイトル:"軽量なソリューションの読み込み (LSL) |Microsoft ドキュメント"ms.custom:""ms.date::「01/17/2017」ms.reviewer:""ms.suite:""ms.technology:: 
  - "vs ide sdk"ms.tgt_pltfrm:""ms.topic:: helpviewer_keywords を「記事」。 
  - Vspackage、軽量なソリューションの読み込み」
  - 「Vspackage には、ソリューションの読み込みが高速な」ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1 caps.latest.revision: 1 作成者:"gregvanl"ms.author:"gregvanl"マネージャー: ghogen
---
# <a name="lightweight-solution-load-lsl"></a>軽量のソリューションの読み込み (LSL)

## <a name="background-information-on-lsl"></a>LSL の背景情報について

VS 2017 年ソリューションの読み込み時間が大幅に低下すると、すぐに生産性を向上させるを有効にするの新機能は、軽量なソリューションを読み込みます。 LSL を有効にすると、Visual Studio は完全に読み込まれませんプロジェクトに作業を開始するまで。

LSL Visual Studio 拡張機能に影響を与えることができます。 読み込まれるプロジェクトに依存してフィーチャーを持つ拡張機能の動作または従わず、このドキュメントで詳細なガイダンスは、正常に動作しない可能性がありますできません。

さらにバック グラウンドで LSL、次のリンクを使用します。

* [簡易ソリューション ロード ブログ](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* 質問ですか。 ご連絡ください。[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>「遅延」モードでのプロジェクトを読み込む設定を有効にします。

1. 現在開いているソリューションを閉じます。
2. 移動して**ツール** > **オプション** > **プロジェクトおよびソリューション** > **全般**設定ページです。
3. チェック、**軽量のソリューションの読み込み**ボックス設定を有効にします。

上の設定をオンになっているソリューションが開かれると、IDE、プロジェクトの通常のビューを示していますが、プロジェクトが読み込まれていません。

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>遅延読み込みとプロジェクトの読み込みの正規の相違点

ライトウェイト ソリューションの読み込みと、ソリューションを開くときに、プロジェクトは読み込まれません。 これら「遅延のプロジェクト」スタブ階層が作成されます。 ソリューション エクスプ ローラーが、一部またはすべてのプロジェクトは「遅延モード」で、UI の表示アイコンと、プロジェクトの名前と予想されるビューを示します。

LSL が有効になっている、操作がトリガーされたときに、必要なプロジェクトを既に完全に読み込まれている不要になった拡張機能が予想できます。 呼び出し元は、読み込まれたプロジェクトの依存関係があるかどうかを確認する必要があります。 拡張機能は、遅延のプロジェクトからの情報を必要とする場合、拡張機能は、次を行います。

1. 必要に応じて、プロジェクトを読み込みます。
2. 使用して、新しい**ワークスペース Api**それを読み込むことがなく遅延プロジェクトから情報を取得します。

新しい**ワークスペース Api**遅延プロジェクトからソース ファイルと指定したプロジェクトのソース ファイルのすべての所有しているプロジェクトなどの情報を取得する拡張を許可します。 場合によっては、プロジェクトの限定されたセットのみをロードする必要があります。 適切なオプションは、操作の頻度、別の方法と全体的なユーザー エクスペリエンスの簡単さのバランスです。

すべてのプロジェクトおよびソリューションの読み込みの関連イベントが引き続き LSL モードで発生します。 これにより、VS から予期しない動作を取得するコンポーネントと、これらのプロジェクトが読み込まれる場合と同じ方法で動作します。 プロジェクトの読み込みは、開いているソリューションの中に行われる作業が大幅に軽減も関連します。

## <a name="ui-requirements-and-changes"></a>UI の要件と変更

すべての UI は、等しいとして読み込まれ、遅延のプロジェクトを処理する必要があります。 つまり、読み込まれたプロジェクトで実行できる任意のアクションは、いくつかの例外、遅延のプロジェクトに適用する必要があります。 これを実現する機能のため、既存のプラットフォーム Api、および新しい Api の概要に変更があります。

### <a name="expectations-for-ui"></a>UI の要件

1. 機能は、visual 違いありませんによってプロジェクトが読み込まれたまたは遅延を示す必要があります。
2. 任意の一覧またはソリューションの読み込まれたプロジェクト経由で列挙には、遅延プロジェクトを含める必要があります。
3. 読み込まれたプロジェクトに対して使用可能な任意のアクションを遅延プロジェクトに対して使用できます。
4. 必須の機能の読み込み要求される場合にのみのプロジェクトします。
  * ユーザーの直接の対話機能があります。 プロジェクトをプリエンプティブ ロードしません。
  * 」「結果は」ジェスチャがユーザーによって行われます。 この UI ガイドラインは、以下を参照してください。
  * アクションを満たすには、完全に読み込まれるプロジェクトのみを使用できます。 LSL と、可能な限り、開いているプロジェクト Api を使用し、機能の要求では、機能が不足している場合が要求を送信します。

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>プラットフォームに使用できるドライブ UI Api での変更

1. ソリューションの読み込みのライトウェイト モードとプロジェクトの数が遅延状態で開かれたかどうか、ソリューションを確認する、新しい Api が提供されます。
2. 遅延のすべてのプロジェクトがソリューションに読み込まれるときに、新しいイベントに提供されます。
3. 遅延かどうか、プロジェクトを確認してください、新しい Api が提供されます。
4. 読み込まれたプロジェクトを求めるときに、遅延のプロジェクトを含めるには、既存の Api が更新されます。
5. 既存の Api が更新され、高速ソリューションが完全に読み込まれたソリューションが開かれた後にします。

### <a name="how-to-add-see-more-results-for-a-feature"></a>機能」を参照してください結果は「を追加する方法。

プロジェクトの内容でクエリを実行する機能には、遅延のプロジェクトの影響を考慮する必要があります。 場合によっては、機能から取得できます、クエリの結果 LSL およびワークスペース Api プロジェクトの遅延。 その他の場合は、特定機能の制限事項はプロジェクトが読み込まれる必要があります。 このような状況の両方のプロジェクトと再度クエリを完全に読み込みできる新しい」「結果は」ジェスチャを提供します。 このジェスチャを使用すると、プロジェクトは、実際に読み込まれるときに最適な結果を取得する方法をユーザーに提供中に遅延プロジェクトがある場合に最も近いを与えるに機能します。

機能の一般的なアルゴリズムは次のようになります。

### <a name="when-the-query-is-performed-over-a-single-project"></a>1 つのプロジェクトに対してクエリを実行する場合

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>ソリューション全体に対してクエリを実行する場合

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((int)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>API の変更

### <a name="new-api"></a>新しい API

(Out 遅延の bool) IVsSolution7.IsSolutionLoadDeferred

遅延モードで、現在のソリューションが読み込まれている場合に true を返します。 注ソリューション最初に読み込まれた場合は遅延のモードの場合でも、遅延のすべてのプロジェクトは、最終的に読み込まれている、現在のセッションで (ユーザーの明示的なジェスチャまたは操作によって強制による)、このプロパティはやはり true を返します。

__VSPROPID7 です。VSPROPID_DeferredProjectCount

遅延モードで現在のプロジェクトの数を返します。 このプロパティは、範囲 [0, VSPROPID_ProjectCount] の値があります。

__VSHPROPID9 です。VSHPROPID_IsDeferred

プロジェクト階層とは、遅延読み込み状態の場合は true を返します。

値を EPF_DEFERRED し EPF_NOTDEFERRED __VSENUMPROJFLAGS3

これらのフラグに渡すことが[IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx)遅延と遅延なしのプロジェクトを繰り返し処理します。

### <a name="new-events"></a>新しいイベント

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

このイベントは、遅延のすべてのプロジェクトが読み込まれた後に発生します。 この時点では、VSPROPID_DeferredProjectCount は 0 です。 このイベントは、メモは、ソリューションの読み込みの一部として発生しは発生しません。 すべてのセッションでします。 遅延のすべてのプロジェクトが読み込まれた場合にのみ発生します。

### <a name="changes-to-existing-api"></a>既存の API への変更

* 渡す[__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx)です。EPF_LOADEDINSOLUTION [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx)を返しますがプロジェクトを延期します。
* 渡す[__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx)です。EPF_UNLOADEDINSOLUTION には、遅延のプロジェクトは返しません。
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx)に設定されているソリューションが開いている場合は true です。 遅延のプロジェクトを扱うため、このコンテキストは多くを設定が読み込まれると非 LSL モードでより前です。
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx)です。VSPROPID_ProjectCount では、プロジェクトが読み込まれ、遅延の合計を返します。

## <a name="helpful-code-snippets"></a>便利なコード スニペット

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>遅延読み込みモードで、ソリューションが開かれたかどうかの確認します。

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>プロジェクトが遅延しているかどうかの確認します。

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>プロジェクトを読み込み

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>一連のプロジェクトを読み込む

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>プロジェクト、ソリューションの遅延かどうかを確認します。

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>ワークスペースの Api を使用した詳細な情報を取得します。

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>LSL ソリューションに関する詳細情報を表示する方法

ワークスペースの新しい Api は、ソリューションに関する詳細情報を取得できるようにする IVsSolutionWorkspaceService を介して公開されます。

これらの Api を使用してをワークスペースのインデックス サービスに加え、現在のワークスペース、アクティブなソリューション、コマンドラインのマネージ情報を取得できます。 これらの Api は、インデックスの詳細のデータを取得するサービスをすべてのソース ファイル、ソース ファイルの所有しているプロジェクトのプロジェクトですべてのプロジェクトが、現在のソリューションに含まれているプロジェクトなどのすべての P2P 参照をさらに活用できます。

次のコード スニペットでは、ワークスペース Api の使用方法を示します。

### <a name="get-ivssolutionworkspaceservice-initially"></a>IVsSolutionWorkspaceService を最初に取得します。

>**注:**ワークスペース API パッケージの読み込みを回避する LSL シナリオで IVsSolutionWorkspaceService ののみ入手してください。

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**注:** _solutionWorkspaceService が既に遅れて初期化される次のスニペットがあるとします。

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>アクティブ ソリューション構成の遅延のプロジェクトの管理対象のコマンド ライン情報を取得します。

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>LSL でアクティブなソリューション ファイルを取得します。

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>請け負っているプロジェクトのソース ファイルを取得します。

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>プロジェクトからのすべてのソース ファイルを取得します。

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>プロジェクトでの P2P 参照を取得します。

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>ソリューション内のすべてのプロジェクトを取得します。

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>トラブルシューティング

LSL の性質上、ユーザーが読み込まれ、遅延のプロジェクトの違いを表示できません意図的なものです。 これにより、機能の開発とテストが困難。

遅延のプロジェクトの UI でビジュアルのヒントを有効にするには、次の操作します。

1. Visual Studio を閉じます。
2. Regedit.exe
3. HKLM を選択します。
4. ファイル > ハイブの読み込み
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. キー名として"VisualStudio"を入力してください。
7. 設定`HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1`(DWORD)
8. HKLM\VisualStudio を選択します。
9. ファイル > ハイブのアンロード
10. Visual Studio を起動します。

さらに、質問についてにお問い合わせください[ lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)です。






