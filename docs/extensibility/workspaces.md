---
title: Visual Studio でワークスペース |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 0230201677fd2422817ca1fbeab6679a424e5c05
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31145972"
---
# <a name="workspaces"></a>ワークスペース

ワークスペースとは、Visual Studio がファイル内の任意のコレクションを表す方法[フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)で表されますが、<xref:Microsoft.VisualStudio.Workspace.IWorkspace>型です。 自体は、ワークスペースは、内容やフォルダー内のファイルに関連する機能を理解していません。 代わりに、一般的な機能と拡張機能を作成し、他のユーザーを操作できるデータを使用する Api のセットを提供します。 プロデューサーが経由で構成されて、 [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) を使用してさまざまな属性をエクスポートします。

## <a name="workspace-providers-and-services"></a>ワークスペースのプロバイダーとサービス

ワークスペースのプロバイダーとサービスは、データと、ワークスペースの内容に反応するための機能を提供します。 コンテキストのファイルについては、ソース ファイル内のシンボルを提供または機能を構築する可能性があります。

両方の概念を使用して、[ファクトリ パターン](https://en.wikipedia.org/wiki/Factory_method_pattern)されワークスペースによって MEF からインポートされます。 エクスポートのすべての属性を実装`IProviderMetadataBase`または`IWorkspaceServiceFactoryMetadata`がエクスポートされた型の拡張機能が使用する具体的な種類があります。

プロバイダーとサービスの 1 つの違いは、ワークスペースの関係です。 ワークスペースでは、特定の型の多くのプロバイダーを使用できますが、ワークスペースあたり特定の種類の 1 つのサービスを作成します。 たとえば、ワークスペースには、多くのファイル スキャナー プロバイダーがワークスペースは、ワークスペースあたり 1 つだけのインデックス作成サービスがします。

別の大きな違いは、プロバイダーやサービスからのデータの消費量です。 ワークスペースは、プロバイダーからのいくつかの理由からデータを取得するエントリ ポイントです。 最初に、通常、プロバイダーでは、幅の狭い一連の一部を作成するデータがあります。 データか可能性が c# ソース ファイルのシンボルのファイルのコンテキストを構築、 _CMakeLists.txt_ファイル。 ワークスペースには、要求と整合してメタデータを持つプロバイダーのコンシューマーの要求が反映されます。 次に、いくつかのシナリオでは、多くのシナリオの他の要求に貢献するプロバイダーは、優先度が高いプロバイダーを使用します。

これに対し、拡張機能はインスタンスを取得し、ワークスペースのサービスと直接やり取りできます。 拡張メソッド`IWorkspace`など、Visual Studio によって提供されるサービスで利用できるは<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>します。 拡張機能には、拡張機能内のコンポーネントまたは他の拡張機能を使用するは、ワークスペース サービスを提供できます。 コンシューマーを使用する必要があります<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A>またはで指定した拡張メソッド、`IWorkspace`型です。

>[!WARNING]
> Visual Studio と競合するサービスを作成していません。 予期しない問題になることができます。

## <a name="disposal-on-workspace-closure"></a>ワークスペースの終了時に廃棄

ワークスペースのクロージャは、extender が必要になる dispose が非同期に呼び出すことはコード。 <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>インターフェイスを使用して、このコードを簡単に記述します。

## <a name="related-types"></a>関連する型

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> 開いているフォルダーのように、開かれているワークスペースの中央のエンティティです。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> インスタンス化されたワークスペースあたりプロバイダーを作成します。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> ワークスペースがインスタンス化ごとのサービスを作成します。
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> プロバイダーおよび破棄処理中に非同期コードを実行する必要があるサービスで実装する必要があります。
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> 既知のサービスまたは任意のサービスにアクセスするためのヘルパー メソッドを提供します。

## <a name="workspace-settings"></a>ワークスペースの設定

ワークスペースが、<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager>をワークスペースに簡易かつ強力な制御サービス。 設定の基本的な概要については、次を参照してください。[ビルドをカスタマイズし、タスクをデバッグ](../ide/customize-build-and-debug-tasks-in-visual-studio.md)です。

ほとんどの設定を`SettingsType`型は _.json_など_VSWorkspaceSettings.json_と_tasks.vs.json_です。

ワークスペースの設定の電源を「スコープ」は、ワークスペース内のパスだけでは、中心にします。 コンシューマーを呼び出すと<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>、要求されたパスと設定の種類を含むすべてのスコープは集計します。 スコープの集計の優先度は次のとおりです。

1. ワークスペースのルートは、通常「ローカル設定」`.vs`ディレクトリ。
1. 要求されたパス自体です。
1. 要求されたパスの親ディレクトリです。
1. すべてさらに、ワークスペースのルートを含むディレクトリの親です。
1. ユーザーのディレクトリには、「グローバル設定」。

結果のインスタンスである<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>です。 このオブジェクトが特定の種類の設定を保持し、として格納されているキー名を設定するために問い合わせることができます`string`です。 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A>メソッドと<xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions>拡張メソッドが要求する呼び出し元が要求されている設定値の型を認識します。 ほとんどの設定ファイルとして永続化と _.json_ファイル、多くの呼び出しが使用`string`、 `bool`、 `int`、およびそれらの型の配列。 オブジェクトの種類もサポートします。 使用できるような場合、`IWorkspaceSettings`自体の型引数として。 例えば:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

ユーザーのこれらの設定を想定していた_VSWorkspaceSettings.json_、として、データにアクセスできます。

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>これらの設定の Api とは無関係で利用可能な Api、`Microsoft.VisualStudio.Settings`名前空間。 ワークスペースの設定は、ホストの柔軟なワークスペースに固有の設定ファイルまたは動的な設定プロバイダーを使用します。

### <a name="providing-dynamic-settings"></a>動的な設定を提供します。

拡張機能を提供できる<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s。 これらのメモリ内のプロバイダーでは、拡張機能の設定を追加または他のユーザーをオーバーライドできるようにします。

エクスポート、`IWorkspaceSettingsProvider`他のワークスペース プロバイダーとは異なります。 ファクトリが`IWorkspaceProviderFactory`特別な属性の型はありません。 代わりに、実装<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory>して`[Export(typeof(IWorkspaceSettingsProviderFactory))]`です。

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>返すメソッドを実装するときに`IWorkspaceSettingsSource`(と同様に`IWorkspaceSettingsProvider.GetSingleSettings`) のインスタンスを返す`IWorkspaceSettings`なく`IWorkspaceSettingsSource`です。 `IWorkspaceSettings` 詳細については、いくつかの設定の集計中に役に立ちますを提供します。

### <a name="settings-related-apis"></a>設定関連 Api

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> 読み取り、ワークスペースの設定を集計します。
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> 取得、`IWorkspaceSettingsManager`ワークスペースのです。
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> 重複しているすべてのスコープから集計された特定のスコープの設定を取得します。
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> 特定のスコープの設定が含まれています。

## <a name="workspace-suggested-practices"></a>ワークスペースに推奨されるプラクティス

- オブジェクトを返す`IWorkspaceProviderFactory.CreateProvider`または同様の Api に注意してください、`Workspace`コンテキストの作成時にします。 プロバイダーのインターフェイスは、このオブジェクトが作成時に保持される必要が書き込まれます。
- ワークスペースに固有のキャッシュまたはワークスペースの [ローカル設定] のパス内の設定を保存します。 使用して、ファイルのパスを作成する`Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder`Visual Studio 2017 15.6 またはそれ以降のバージョンにします。 バージョン 15.6 より前のバージョンでは、次のスニペットを使用します。

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>ソリューションのイベントとパッケージの自動読み込み

読み込まれたパッケージを実装できます`IVsSolutionEvents7`を呼び出すと`IVsSolution.AdviseSolutionEvents`です。 Visual Studio でのフォルダーを開いたり閉じたりでイベントが含まれています。

UI コンテキストは、パッケージの自動読み込みを使用できます。 値が `4646B819-1AE0-4E79-97F4-8A8176FDD664` です。

## <a name="troubleshooting"></a>トラブルシューティング

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage パッケージは正しく読み込まれませんでした。

ワークスペースの機能拡張は頻度の高い MEF に基づいており、コンポジション エラーが発生する、パッケージの読み込み失敗を開いているフォルダーをホストします。 たとえば、拡張機能を持つ型をエクスポートする`ExportFileContextProviderAttribute`、型が実装のみが、 `IWorkspaceProviderFactory<IFileContextActionProvider>`、Visual Studio でのフォルダーを開こうとしたときにエラーが発生します。 エラーの詳細は含まれて _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_です。 拡張機能によって実装されている種類のエラーを解決します。

## <a name="next-steps"></a>次の手順

* [ファイルのコンテキスト](workspace-file-contexts.md)-ファイル コンテキスト プロバイダーは、のワークスペースでフォルダーを開くコード インテリジェンスを表示します。 
* [インデックス作成](workspace-indexing.md)-インデックスの作成 ワークスペースを収集し、ワークスペースの概要情報が引き続き発生します。
