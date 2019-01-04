---
title: Visual Studio でワークスペース ファイル コンテキスト |Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 93690eab989cee62d756a774675bf1d46da017fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826865"
---
# <a name="workspace-file-contexts"></a>ワークスペース ファイルのコンテキスト

すべての洞察[フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)ワークスペースは、"ファイル コンテキスト"を実装するプロバイダーによって生成される、<xref:Microsoft.VisualStudio.Workspace.IFileContextProvider>インターフェイス。 これらの拡張機能がフォルダー内のパターンを検索または MSBuild ファイルとメイクファイル、読み取るファイルはファイルのコンテキストを定義する必要な分析情報を蓄積するためにパッケージの依存関係などを検出します。 単独でのファイル コンテキストは、任意の処理は行われませんが、データの操作を実行できます別の拡張機能を提供します。

各<xref:Microsoft.VisualStudio.Workspace.FileContext>が、`Guid`に関連付けられているデータの種類を識別することが実行されます。 ワークスペースがこれを使用して`Guid`以降を拡張機能を使用してデータを使用すると照合し、<xref:Microsoft.VisualStudio.Workspace.FileContext.Context>プロパティ。 ファイル コンテキストのプロバイダーは、どのファイル コンテキストを識別するメタデータと共にエクスポートされる`Guid`s のデータがあります。

定義と、ファイルのコンテキストではファイルまたはフォルダー、ワークスペース内の任意の数を関連付けることができます。 指定されたファイルまたはフォルダーは、ファイルのコンテキストの任意の数を関連付けることができます。 多対多リレーションシップです。

ファイルのコンテキストの最も一般的なシナリオは、ビルド、デバッグ、および言語サービスに関連します。 詳細については、これらのシナリオに関連するその他のトピックを参照してください。

## <a name="file-context-lifecycle"></a>ファイル コンテキストのライフ サイクル

ライフ サイクルを`FileContext`が非決定的です。 いつでも、コンポーネントを非同期的にコンテキストの種類のいくつかのセットを要求できます。 要求コンテキストの種類のサブセットをサポートするプロバイダーは照会されます。 `IWorkspace`インスタンスは、コンシューマーとプロバイダー間の仲介として機能します、<xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A>メソッド。 コンシューマーは、コンテキストを要求し、他のユーザー コンテキストを要求して長期的な参照を保持可能性があります、コンテキストに基づくの短期的なアクションを実行可能性があります。 

変更は、古くなる場合がファイルのコンテキストとなるファイルが発生する可能性があります。 プロバイダーでイベントを発生させることができます、`FileContext`更新プログラムのコンシューマーに通知します。 たとえば、いくつかのファイルのビルド コンテキストが提供されている場合は、ディスク上の変更をそのコンテキストが無効になりますし、元のプロデューサーもイベントに呼び出すことができます。 まだを参照しているすべてのコンシューマー`FileContext`新しいできますし、クエリを再実行`FileContext`します。

>[!NOTE]
>コンシューマーにプッシュ モデルはありません。 コンシューマーはプロバイダーの新しい通知されず`FileContext`要求の後です。

## <a name="expensive-file-context-computations"></a>コストのかかるファイル コンテキストの計算

ディスクからファイルの内容を読み取り、プロバイダーは、ファイル間の関係を解決する必要がある場合に特に、高価なことはできます。 たとえば、プロバイダーを照会するには、いくつかのソース ファイルのファイル コンテキストが、ファイルのコンテキストでは、プロジェクト ファイルからのメタデータに依存します。 プロジェクト ファイルの解析や MSBuild での評価は、高価なです。 拡張機能を代わりに、エクスポートすることができます、`IFileScanner`を作成する`FileDataValue`ワークスペースがインデックス作成時にデータ。 今すぐファイルのコンテキストを求められたら、`IFileContextProvider`インデックス付きデータをすばやく照会できます。 インデックス作成の詳細については、次を参照してください。、[ワークスペース インデックス](workspace-indexing.md)トピック。

>[!WARNING]
>その他の方法に注意してください、`FileContext`を計算する高価な場合があります。 一部の UI 操作は同期され、大量の依存`FileContext`要求。 例としては、エディターのタブを開き、開く、**ソリューション エクスプ ローラー**コンテキスト メニュー。 これらのアクションは、多くのビルド コンテキストが入力要求を確認します。

## <a name="file-context-related-apis"></a>ファイルのコンテキストに関連する Api

- <xref:Microsoft.VisualStudio.Workspace.FileContext> データおよびメタデータを保持します。
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1>ファイル コンテキストを作成します。
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> ファイルのコンテキスト プロバイダーをエクスポートします。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> ファイルのコンテキストを取得するコンシューマーに使用されます。
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> 開いているフォルダーが消費するビルド コンテキストの種類を定義します。

## <a name="file-context-actions"></a>ファイル コンテキスト アクション

中に、`FileContext`自体は、一部のファイルについてだけでデータを<xref:Microsoft.VisualStudio.Workspace.IFileContextAction>express し、そのデータを操作する方法です。 `IFileContextAction` 使用量は柔軟性があります。 その最も一般的なケースの 2 つのビルドとデバッグされます。

## <a name="reporting-progress"></a>進行状況の報告

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>メソッドに渡されます`IProgress<IFileContextActionProgressUpdate>`がその型と引数を使用しないでください。 `IFileContextActionProgressUpdate` 空のインターフェイスは、呼び出す`IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)`をスローする可能性`NotImplementedException`します。 代わりに、`IFileContextAction`シナリオでは、必要に応じて別の型引数をキャストする必要があります。

Visual Studio によって提供される型については、それぞれのシナリオのドキュメントを参照してください。

## <a name="file-context-action-related-apis"></a>ファイル コンテキスト アクション関連 Api

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> 基づくいくつかの動作を実行する`FileContext`します。
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> インスタンスを作成`IFileContextAction`です。
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> 種類をエクスポート`IWorkspaceProviderFactory<IFileContextActionProvider>`します。

## <a name="file-watching"></a>ファイルの監視

ワークスペースがファイル変更通知をリッスンし、提供、<xref:Microsoft.VisualStudio.Workspace.IFileWatcherService>を介して<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>します。 "ExcludedItems"設定に一致するファイルでは、ファイルの通知のイベントは生成されません。 イベントの間のしきい値は、通知の簡略化し、重複の削減に使用されます。 ファイルの変更に対応する必要がある場合は、このサービスにサブスクライブする必要があります。

>[!TIP]
>ワークスペースの[インデックス サービス](workspace-indexing.md)既定では、ファイルのイベントをサブスクライブします。 ファイルの追加と変更と関連する、`IFileScanner`のイベントは、そのファイルの新しいデータに対して呼び出すことができます。 ファイルの削除をインデックス付きデータが削除されます。 サブスクライブする必要はありません、`IFileScanner`ファイルの監視サービスにします。

## <a name="next-steps"></a>次の手順

* [インデックス作成](workspace-indexing.md)-ワークスペースのインデックスを収集し、ワークスペースに関する情報が保持されます。
* [ワークスペース](workspaces.md)-ワークスペースの概念と設定の保存場所を確認します。
