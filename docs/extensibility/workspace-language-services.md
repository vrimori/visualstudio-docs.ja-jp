---
title: ワークスペースと Visual Studio での言語サービス |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 551a621ab97c232970d6ef67da14379c5cdfbd46
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140808"
---
# <a name="workspaces-and-language-services"></a>ワークスペースおよび言語サービス

言語サービスを提供できます[フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)ユーザーと同じ言語の機能豊富な機能は使用するソリューションとプロジェクトを操作するときにします。 言語サービスがアクティブ化する自己基づいていますファイル拡張子、開いているドキュメントの内容がこの「厳密でないファイル」言語サービスは、構文の強調表示に制限されます。 ソース コードの編集/表示するときに、豊富なエクスペリエンスを提供する追加情報が必要です。 各言語サービスには、ドキュメントのこの余分なコンテキストのデータと初期化の独自の API があります。 これは通常、言語サービスと、ビルド システムの両方は密接に関連するプロジェクト システムによって管理されます。

## <a name="initialization"></a>初期化

[ワークスペース](workspaces.md)、言語サービスは初期化されて、<xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider>言語サービスでのみを特化、ビルドのオーサリングを一切把握拡張ポイントです。 これにより、言語サービスの所有者は、フォルダーと (たとえば MSBuild、メイクファイルなど) のビルド時に、コンパイラを実行するためのファイル内でどのようにいくつかのパターンに関係なく拡張が存在する単一の開いているフォルダーを管理できます。 ファイルのコンテキストの作成元のファイルがディスク上で変更すると、ファイルのコンテキストが更新される、更新されたファイルのコンテキストのセット、言語サービス プロバイダーが通知されます。 言語サービス プロバイダーは、そのモデルを更新できます。

エディターでドキュメントを開いたときに Visual Studio のみを考慮する言語を一致するファイル コンテキスト プロバイダーを入手できますファイル コンテキストの種類を必要とするサービス プロバイダー。 次に、渡しますファイル コンテキスト一致するプロバイダーから、選択した言語サービス プロバイダー経由で`ILangaugeServiceProvider.InitializeAsync`です。 言語サービス プロバイダーが何をするファイルのコンテキスト データが言語サービス プロバイダーの実装の詳細が、必要なユーザー エクスペリエンスの高度な言語サービスには、ドキュメントが開かれます。

## <a name="using-ilanguageserviceprovider"></a>ILanguageServiceProvider を使用します。

ファイルのコンテキストが作成されたとき、言語サービスに通知する、`ContextType`のいずれかに一致する、`SupportedContextTypes`言語のサーバーの値が属性をエクスポートします。

言語サービスをサポートするには、拡張機能は必要があります。

- 一意な`Guid`します。 これは、使用`SupportedContextTypes`属性の引数と、`FileContext`オブジェクト。
- 言語ファイルのコンテキスト
  - プロバイダー ファクトリ
    - `ExportFileContextProviderAttribute` 上記の属性が生成される一意`Guid`で `SupportedContextTypes`
    - 実装 `IWorkspaceProviderFactory<IFileContextProvider>`
  - プロバイダーの実装 `IFileContextProvider.GetContextsForFileAsync`
    - 新しい構築`FileContext`で、`contextType`として一意に生成されたコンス トラクターの引数 `Guid`
    - 使用して、`Context`のプロパティ、`FileContext`に追加のデータを提供する、 `ILanguageServiceProvider`
- 言語サービス
  - プロバイダー ファクトリ
    - `ExportLanguageServiceProvider` 上記の属性が生成される一意`Guid`で `SupportedContextTypes`
    - 実装 `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - プロバイダー
    - 実装 `ILanguageServiceProvider`
    - 使用して`ILanguageServiceProvider.InitializeAsync`ファイルが開かれたときに、指定された引数の言語サービスを有効にするには
    - 使用して`ILanguageServiceProvider.UninitializeAsync`ファイルが閉じられたときに、指定された引数の言語サービスを無効にするには

>[!WARNING]
>`ILanguageServiceProvider`のメソッドは、メイン スレッド上のワークスペースから呼び出すことがあります。 UI の遅延を防ぐには異なるスレッドでの作業をスケジュール設定を検討してください。

## <a name="language-server-protocol"></a>言語のサーバー プロトコル

`Microsoft.VisualStudio.Workspace.*` Api は開いているフォルダーに、言語サービスを有効にする唯一の方法です。 言語サーバーを使用することもできます。 詳細については、に関する記事を参照、[言語サーバー プロトコル](language-server-protocol.md)です。

## <a name="related-interfaces"></a>関連するインターフェイス

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> 一致するファイルの種類のファイルを開くか編集用に開いていないときに呼び出されます。

## <a name="next-steps"></a>次の手順

* [ワークスペース ビルド](workspace-build.md)-MSBuild とメイクファイルなどのシステムをビルド フォルダーを開く。 