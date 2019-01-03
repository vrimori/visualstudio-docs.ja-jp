---
title: Visual Studio のワークスペース |Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 406d55b773a586d5cb0128599e225dabbadf21d3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876904"
---
# <a name="workspaces"></a>ワークスペース

ワークスペースとは、Visual Studio でのファイルの任意のコレクションを表す方法[フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)、によって表現されていると、<xref:Microsoft.VisualStudio.Workspace.IWorkspace>型。 単独で、ワークスペースは、コンテンツまたはフォルダー内のファイルに関連する機能を理解していません。 代わりに、生成および他のユーザーが対処できるデータを使用する機能と拡張機能の Api の一般的なセットを提供します。 プロデューサーは経由で構成される、 [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) を使用してさまざまな属性をエクスポートします。

## <a name="workspace-providers-and-services"></a>ワークスペースのプロバイダーとサービス

ワークスペースのプロバイダーとサービスは、データと、ワークスペースの内容に対応するための機能を提供します。 ソース ファイルでシンボル ファイルのコンテキスト情報を提供または機能を構築する可能性があります。

両方の概念を使用して、[ファクトリ パターン](https://en.wikipedia.org/wiki/Factory_method_pattern)と、ワークスペースによって MEF からインポートされます。 すべてのエクスポート属性の実装`IProviderMetadataBase`または`IWorkspaceServiceFactoryMetadata`、エクスポートされた型の拡張機能が使用する具体的な種類がありますが、します。

プロバイダーとサービス間の違いの 1 つは、ワークスペースの関係です。 ワークスペースでは、特定の型の多くのプロバイダーを使用できますが、ワークスペースごとに特定の種類の 1 つのサービスを作成します。 たとえば、ワークスペースがスキャナーのファイル プロバイダーの多くがワークスペースには、ワークスペースごとの 1 つだけのインデックス作成サービスが用意されています。

もう 1 つの主な違いは、プロバイダーとサービスからのデータの消費量です。 ワークスペースは、プロバイダーからデータをいくつかの理由を取得するエントリ ポイントです。 最初に、通常、プロバイダーでは、いくつか作成するデータのセットがあります。 データ可能性がある c# ソース ファイルのシンボルまたはファイル コンテキストを構築、 _CMakeLists.txt_ファイル。 ワークスペースには、コンシューマーの要求プロバイダーのメタデータを持つ要求の連携には一致します。 多くのいくつかのシナリオを許可する第 2 に、シナリオ中に他のユーザーの要求を投稿するプロバイダーが最も高い優先順位で、プロバイダーを使用します。

これに対し、拡張機能はインスタンスを取得し、ワークスペースのサービスと直接対話できます。 拡張メソッドを`IWorkspace`など、Visual Studio によって提供されるサービスの利用<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>します。 拡張機能、拡張機能内のコンポーネントまたは他の拡張機能を使用するは、ワークスペース サービスを提供できます。 コンシューマーを使用する必要があります<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A>または拡張メソッドが提供する、`IWorkspace`型。

>[!WARNING]
> Visual Studio と競合するサービスを作成していません。 予期しない問題になることができます。

## <a name="disposal-on-workspace-closure"></a>ワークスペースの終了時に破棄

Dispose が非同期に呼び出す必要があります、ワークスペースのクロージャは、エクステンダーのコード。 <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>インターフェイスを簡単にこのコードを記述できるようにするに使用できます。

## <a name="related-types"></a>関連する型

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> 開かれているフォルダーと同様に、開かれているワークスペースのサーバーの全体のエンティティです。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> ワークスペースがインスタンス化ごとのプロバイダーを作成します。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> ワークスペースがインスタンス化ごとのサービスを作成します。
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> プロバイダーおよび破棄中に非同期コードを実行する必要があるサービスで実装する必要があります。
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> よく知られているサービスまたは任意のサービスにアクセスするためのヘルパー メソッドを提供します。

## <a name="workspace-settings"></a>ワークスペースの設定

ワークスペースが、<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager>をワークスペースに単純ながらも強力な制御サービス。 設定の基本的な概要については、次を参照してください。[ビルドのカスタマイズとタスクのデバッグ](../ide/customize-build-and-debug-tasks-in-visual-studio.md)します。

ほとんどの設定`SettingsType`型は _.json_ファイルなど、 _VSWorkspaceSettings.json_と_tasks.vs.json_します。

ワークスペースの設定の機能を中心に「スコープ」は、ワークスペース内のパスだけです。 コンシューマーを呼び出すと<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>設定の種類と要求されたパスが含まれるすべてのスコープが集計されます。 スコープの集計の優先順位は次のとおりです。

1. ワークスペースのルートでは通常「ローカル設定」`.vs`ディレクトリ。
1. 要求されたパス自体。
1. 要求されたパスの親ディレクトリです。
1. さらにすべてを含むワークスペースのルート ディレクトリを親します。
1. ユーザーのディレクトリには、「グローバル設定」。

結果のインスタンスである<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>します。 このオブジェクトは、特定の種類の設定を保持し、として格納されているキー名を設定するために照会できる`string`します。 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A>メソッドと<xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions>拡張メソッドが要求されている設定値の型を認識する呼び出し元を期待します。 ほとんどの設定ファイルとして永続化 _.json_多くの呼び出しで使用するファイル、 `string`、 `bool`、 `int`、およびそれらの型の配列。 オブジェクトの種類もサポートされます。 その場合、使用することができます`IWorkspaceSettings`自体の型引数として。 例:

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

これらの設定がユーザーの_VSWorkspaceSettings.json_、として、データにアクセスできます。

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
>これらの Api の設定とは無関係で利用できる Api、`Microsoft.VisualStudio.Settings`名前空間。 ワークスペースの設定は、ホストに依存しないワークスペース固有の設定ファイルまたは動的な設定プロバイダーを使用します。

### <a name="providing-dynamic-settings"></a>動的な設定を提供します。

拡張機能を提供できます<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>秒。 これらのメモリ内プロバイダーでは、拡張機能の設定を追加または他のユーザー オーバーライドを許可します。

エクスポート、`IWorkspaceSettingsProvider`他のワークスペースのプロバイダーとは異なります。 ファクトリがない`IWorkspaceProviderFactory`特別な属性の型はありません。 代わりに、実装<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory>して`[Export(typeof(IWorkspaceSettingsProviderFactory))]`します。

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
>返すメソッドを実装するときに`IWorkspaceSettingsSource`(など`IWorkspaceSettingsProvider.GetSingleSettings`) のインスタンスを返す`IWorkspaceSettings`なく`IWorkspaceSettingsSource`します。 `IWorkspaceSettings` 詳細についてはいくつかの設定の集計中に使用できるを提供します。

### <a name="settings-related-apis"></a>関連する Api の設定

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> ワークスペースの読み取りと集計に設定します。
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> 取得、`IWorkspaceSettingsManager`のワークスペース。
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> すべての重複するスコープにわたって集計の指定されたスコープの設定を取得します。
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> 特定のスコープの設定が含まれています。

## <a name="workspace-suggested-practices"></a>ワークスペースに推奨されるプラクティス

- オブジェクトを返す`IWorkspaceProviderFactory.CreateProvider`または同様の Api に注意してください、`Workspace`コンテキストの作成時にします。 プロバイダーのインターフェイスの作成時にこのオブジェクトが保持される必要が書き込まれます。
- ワークスペースに固有のキャッシュまたはワークスペースの [ローカルの設定] のパス内の設定を保存します。 使用して、ファイルのパスを作成`Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder`で Visual Studio 2017 バージョン 15.6 以降。 バージョン 15.6 より前のバージョンでは、次のスニペットを使用します。

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

読み込まれたパッケージを実装できる`IVsSolutionEvents7`を呼び出すと`IVsSolution.AdviseSolutionEvents`します。 Visual Studio でのフォルダーを開いたり閉じたりでイベントが含まれています。

UI コンテキストは、パッケージの自動読み込みを使用できます。 値が `4646B819-1AE0-4E79-97F4-8A8176FDD664` です。

## <a name="troubleshooting"></a>トラブルシューティング

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage パッケージは正しく読み込まれませんでした。

ワークスペースの機能拡張では、大きく MEF に基づいており、合成エラーが発生する、パッケージの読み込みに失敗の開いているフォルダーをホストします。 たとえば、拡張機能を持つ型をエクスポートします`ExportFileContextProviderAttribute`、型が実装のみが、 `IWorkspaceProviderFactory<IFileContextActionProvider>`、Visual Studio でフォルダーを開こうとしたときにエラーが発生します。 エラーの詳細が記載されて _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_します。 拡張機能によって実装されている種類のエラーを解決します。

## <a name="next-steps"></a>次の手順

* [ファイル コンテキスト](workspace-file-contexts.md)-ファイル コンテキスト プロバイダーは、ワークスペースでフォルダーを開くコードのインテリジェンスを表示します。 
* [インデックス作成](workspace-indexing.md)-ワークスペースのインデックスを収集し、ワークスペースに関する情報が保持されます。
