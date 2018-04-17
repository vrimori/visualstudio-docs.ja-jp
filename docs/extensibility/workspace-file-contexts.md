---
title: Visual Studio でワークスペース ファイル コンテキスト |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: cdb013bb10c72041b03fce43e115806ecb3faeac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-file-contexts"></a>ワークスペースのファイル コンテキスト

すべての洞察[フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)ワークスペースは、"ファイル コンテキスト"を実装するプロバイダーによって生成、<xref:Microsoft.VisualStudio.Workspace.IFileContextProvider>インターフェイスです。 これらの拡張機能がフォルダー内のパターンを検索またはファイルを MSBuild ファイルとメイクファイルを読み取るファイルのコンテキストを定義する必要があります、洞察を蓄積するためになど、パッケージの依存関係を検出します。 単独でファイルのコンテキストでは、任意の操作は実行されませんではなく別の拡張を操作できる、データを提供します。

各<xref:Microsoft.VisualStudio.Workspace.FileContext>が、`Guid`関連付けられているデータの種類を識別することができます。 ワークスペースがこれを使用して`Guid`を介してデータを使用する拡張機能と照合し以降を<xref:Microsoft.VisualStudio.Workspace.FileContext.Context>プロパティです。 ファイル コンテキスト プロバイダーは、どのファイルのコンテキストを識別するメタデータと共にエクスポートされる`Guid`s のデータがあります。

定義すると、ファイルのコンテキストではワークスペースのファイルまたはフォルダーの任意の数を関連付けることができます。 指定したファイルまたはフォルダーは、ファイルのコンテキストの任意の数を関連付けることができます。 多対多リレーションシップです。

ファイルのコンテキストの最も一般的なシナリオは、ビルド、デバッグ、および言語サービスに関連付けられます。 詳細については、これらのシナリオに関連するその他のトピックを参照してください。

## <a name="file-context-lifecycle"></a>ファイルのコンテキストのライフ サイクル

ライフ サイクル、`FileContext`は非決定的関数です。 いつでも、コンポーネントは一部のコンテキストの種類のセットを要求に非同期的にできます。 要求コンテキストの種類のサブセットをサポートするプロバイダーは照会されます。 `IWorkspace`インスタンスは、コンシューマーからプロバイダーと中間 man として機能、<xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A>メソッドです。 コンシューマーは、コンテキストを要求して、短期的なアクションがコンテキストを要求し、長期的な参照を保持して他のユーザーが中に、コンテキストに基づいて実行可能性があります。 

変更は、古くなるファイルのコンテキストとなるファイルが発生する可能性があります。 プロバイダーでイベントを発生させることができます、`FileContext`更新プログラムのコンシューマーに通知します。 たとえば、ファイルのいくつかのビルド コンテキストが提供される場合は、ディスク上の変更は、そのコンテキストを無効になりますし、元のプロデューサー イベントを起動できます。 まだを参照しているすべてのコンシューマー `FileContext` 、新しいできますし、クエリを再実行`FileContext`です。

>[!NOTE]
>コンシューマーにプッシュ モデルはありません。 コンシューマーは、プロバイダーの新しい通知されず`FileContext`要求の後です。

## <a name="expensive-file-context-computations"></a>コストのかかるファイル コンテキストの計算

ディスクから読み取るファイルの内容は、ファイルの間のリレーションシップを解決するのには、プロバイダーが必要な場合は特に、高価なことができます。 たとえば、プロバイダーをいくつかのソース ファイルのファイルのコンテキストを照会する可能性がありますが、ファイルのコンテキストがプロジェクト ファイルからのメタデータに依存します。 プロジェクト ファイルを解析または MSBuild を使用して評価が高くなります。 拡張機能を代わりに、エクスポートすることができます、`IFileScanner`を作成する`FileDataValue`ワークスペースがインデックス作成時にデータ。 今すぐファイル コンテキスト、要求されたときに、`IFileContextProvider`インデックス付きデータを簡単に照会できます。 インデックス作成の詳細については、次を参照してください。、[ワークスペース インデックス](workspace-indexing.md)トピックです。

>[!WARNING]
>その他の方法に注意してください、`FileContext`を計算する高価な場合があります。 一部の UI の対話は同期であり大量の依存`FileContext`要求します。 例としては、エディターのタブを開き、開く、**ソリューション エクスプ ローラー**コンテキスト メニュー。 これらのアクションは、多くのビルド コンテキストの種類は要求を確認します。

## <a name="file-context-related-apis"></a>ファイルのコンテキストに関連する Api

- <xref:Microsoft.VisualStudio.Workspace.FileContext> データおよびメタデータを保持します。
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> および<xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1>ファイル コンテキストを作成します。
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> ファイルのコンテキスト プロバイダーをエクスポートします。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> ファイルのコンテキストを取得するコンシューマーに使用されます。
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> 開いているフォルダーを使用するビルド コンテキストの種類を定義します。

## <a name="file-context-actions"></a>ファイルのコンテキストのアクション

中に、`FileContext`自体は、一部のファイルに関するデータだけで、 <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> express し、そのデータを操作する方法を示します。 `IFileContextAction` 使用率で柔軟性があります。 その最も一般的な事例の 2 つのビルドとデバッグされます。

## <a name="reporting-progress"></a>進行状況レポート

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>メソッドに渡されます`IProgress<IFileContextActionProgressUpdate>`が、引数は、その型として使用するべきではありません。 `IFileContextActionProgressUpdate` 空のインターフェイスは、呼び出す`IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)`スローする可能性があります`NotImplementedException`です。 代わりに、`IFileContextAction`シナリオでは、必要に応じて、別の型の引数をキャストする必要があります。

Visual Studio によって提供される型については、それぞれのシナリオのドキュメントを参照してください。

## <a name="file-context-action-related-apis"></a>ファイルのコンテキストの動作に関連する Api

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> 基づくいくつかの動作を実行、`FileContext`です。
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> インスタンスを作成`IFileContextAction`です。
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> 種類をエクスポート`IWorkspaceProviderFactory<IFileContextActionProvider>`です。

## <a name="file-watching"></a>ファイルの監視

ワークスペースは、ファイル変更通知を受信し、提供、<xref:Microsoft.VisualStudio.Workspace.IFileWatcherService>を介して<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>です。 "ExcludedItems"設定に一致するファイルでは、ファイルの通知のイベントは生成されません。 通知の単純化と重複する削減イベント間でのしきい値が使用されます。 ファイルの変更に反応する必要がある場合は、このサービスをサブスクライブする必要があります。

>[!TIP]
>ワークスペースの[インデックス サービス](workspace-indexing.md)既定では、ファイルのイベントをサブスクライブします。 ファイルの追加および変更すると、関連する`IFileScanner`そのファイルの新しいデータに対して呼び出される s イベント。 ファイルの削除では、インデックス付きデータを削除します。 サブスクライブする必要はありません、`IFileScanner`ファイルの監視サービスにします。

## <a name="next-steps"></a>次の手順

* [インデックス作成](workspace-indexing.md)-インデックスの作成 ワークスペースを収集し、ワークスペースの概要情報が引き続き発生します。
* [ワークスペース](workspaces.md)-ワークスペース概念や記憶域の設定を確認します。
