---
title: Visual Studio でワークスペース ビルド |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: f7415c99c68436519f9bab721fe88a48f750fa1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-build"></a>ワークスペースのビルド

サポートをビルド[フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)シナリオが、extender を指定する必要があります[インデックス](workspace-indexing.md)と[ファイル コンテキスト](workspace-file-contexts.md)データを[ワークスペース](workspaces.md)、としてとして実行するビルド アクション。

拡張機能が必要がありますの概要を次に示します。

## <a name="build-file-context"></a>ファイルのコンテキストをビルドします。

- プロバイダー ファクトリ
  - `ExportFileContextProviderAttribute` 属性が`supportedContextTypeGuids`すべて該当する`string`から定数 `BuildContextTypes`
  - 実装 `IWorkspaceProviderFactory<IFileContextProvider>`
  - ファイルのコンテキストのプロバイダー
    - 返す、`FileContext`ごとにビルド操作およびサポートされている構成
      - `contextType` 差出人 <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` 実装する<xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext>で、`Configuration`としてビルド構成のプロパティ (たとえば`"Debug|x86"`、 `"ret"`、または`null`該当しない場合)。 またはのインスタンスを使用して<xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>です。 構成値**必要があります**インデックスが作成されたデータ値から構成と一致します。

## <a name="indexed-build-file-data-value"></a>インデックス付きのビルド ファイルのデータ値

- プロバイダー ファクトリ
  - `ExportFileScannerAttribute` 属性が`IReadOnlyCollection<FileDataValue>`としてサポートされる型
  - 実装 `IWorkspaceProviderFactory<IFileScanner>`
- 上のファイル スキャナー `ScanContentAsync<T>`
  - データを返すときに`FileScannerTypeConstants.FileDataValuesType`の型引数です
  - それぞれの構成で構築されたファイルのデータ値を返します。
    - `type` as `BuildConfigurationContext.ContextTypeGuid`
    - `context` ビルド構成と (たとえば`"Debug|x86"`、 `"ret"`、または`null`該当しない場合)。 この値**必要があります**ファイル コンテキストからの構成と一致します。

## <a name="build-file-context-action"></a>ビルド ファイルのコンテキストのアクション

- プロバイダー ファクトリ
  - `ExportFileContextActionProvider` 属性が`supportedContextTypeGuids`すべて該当する`string`から定数 `BuildContextTypes`
  - 実装 `IWorkspaceProviderFactory<IFileContextActionProvider>`
- アクション プロバイダー `IFileContextActionProvider.GetActionsAsync`
  - 返す、`IFileContextAction`に一致する、指定された`FileContext.ContextType`値
- ファイルのコンテキストのアクション
  - 実装して`IFileContextAction`と <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` プロパティを返します。 `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` `0x1000`ビルド、`0x1010`の再構築、または`0x1020`のクリーンアップ

>[!NOTE]
>`FileDataValue` 、インデックスを作成する必要がある程度のワークスペースとフル ビルド機能のファイルをスキャンするポイントを開くまでの時間があります。 遅延は、以前にキャッシュされたインデックスがないために、フォルダーの最初に開くで表示されます。

## <a name="reporting-messages-from-a-build"></a>ビルドからのメッセージを報告

ビルドできますサーフェス情報、警告、およびエラー メッセージをユーザーに 2 つの方法のいずれか。 簡単な方法を使用して、<xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService>を提供し、 <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>、次のようにします。

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` および`BuildMessage.LogMessage`ユーザーに情報を表示する場所の動作を制御します。 任意`BuildMessage.TaskType`以外の値`None`が生成されます、**エラー一覧**エントリの詳細を指定します。 `LogMessage` 出力は常に、**ビルド**のペイン、**出力**ツール ウィンドウです。

または、拡張機能と対話できます直接、**エラー一覧**または**ビルド**ウィンドウです。 Visual Studio 2017 バージョン 15.7 より前のバージョンにバグが存在する場所、`pszProjectUniqueName`の引数<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*>は無視されます。

>[!WARNING]
>呼び出し元`IFileContextAction.ExecuteAsync`に任意の基になる実装を提供することができます、`IProgress<IFileContextActionProgressUpdate>`引数。 呼び出さない`IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)`直接です。 現在、この引数を使用するための一般的なガイドラインはありませんが、このガイドラインは、変更される可能性があります。

## <a name="build-related-apis"></a>ビルド関連 Api

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> ビルド構成の詳細を提供します。
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> 表示<xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>ユーザーにします。

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.json と launch.vs.json

Tasks.vs.json または launch.vs.json ファイルの作成方法の詳細については、次を参照してください。[ビルドをカスタマイズし、タスクをデバッグ](../ide/customize-build-and-debug-tasks-in-visual-studio.md)です。

## <a name="next-steps"></a>次の手順

* [言語のサーバー プロトコル](language-server-protocol.md)-Visual Studio に言語のサーバーを統合する方法について説明します。