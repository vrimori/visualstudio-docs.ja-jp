---
title: ワークスペースと Visual Studio での言語サービス |Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 28ecd995446969c271694c554ae21e03c1afc79d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850269"
---
# <a name="workspaces-and-language-services"></a>ワークスペースと言語サービス

言語サービスを提供できます[フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)ユーザーと同じ豊富な言語機能は使用するソリューションとプロジェクトを使用する場合。 言語サービスが自己アクティブ化この「ルース ファイル」言語サービスでは、構文の強調表示に制限されますが、ファイルの拡張機能または開いているドキュメントのコンテンツに基づいて。 ソース コードの編集/レビューするときより豊富なエクスペリエンスを提供する追加情報が必要です。 各言語サービスでは、ドキュメントのこの追加のコンテキストのデータの初期化のための独自の API があります。 これは通常、言語サービスと、ビルド システムの両方が密結合プロジェクト システムによって管理されます。

## <a name="initialization"></a>初期化

[ワークスペース](workspaces.md)、言語サービスが初期化によって、<xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider>専門言語サービスでのみを認識しないビルド作成の拡張ポイント。 これにより、言語サービスの所有者は、数パターンに関係なく、拡張機能が (たとえば MSBuild、メイクファイルなど) のビルド中に、コンパイラを実行するフォルダーとファイル内に存在する 1 つの開いているフォルダーを維持できます。 ディスク上のファイル コンテキストの作成元のファイルを変更して、ファイル コンテキストを更新、更新されたファイルのコンテキストのセット、言語サービス プロバイダーが通知されます。 言語サービスのプロバイダーは、そのモデルを更新できます。

エディターでドキュメントを開くと Visual Studio のみを考慮する言語を一致するファイル コンテキスト プロバイダーを入手できますファイル コンテキストの型を必要とするサービス プロバイダー。 次に渡しますファイル コンテキスト、次の一致するプロバイダーからを使用して、選択した言語サービス プロバイダーに`ILanguageServiceProvider.InitializeAsync`します。 言語サービス プロバイダーが何でファイル コンテキストのデータは、言語サービス プロバイダーの実装の詳細が、想定されるユーザー エクスペリエンスを豊富な言語サービスは、ドキュメントを開いています。

## <a name="using-ilanguageserviceprovider"></a>ILanguageServiceProvider を使用します。

言語サービスにはファイルのコンテキストが作成時に通知を`ContextType`のいずれかに一致する、`SupportedContextTypes`言語のサーバーの値が属性をエクスポートします。

言語サービスをサポートするには、拡張機能が必要です。

- 一意`Guid`します。 これは、使用`SupportedContextTypes`属性の引数と、`FileContext`オブジェクト。
- 言語ファイルのコンテキスト
  - プロバイダー ファクトリ
    - `ExportFileContextProviderAttribute` 上記の属性が生成される一意`Guid`で `SupportedContextTypes`
    - 実装 `IWorkspaceProviderFactory<IFileContextProvider>`
  - プロバイダーの実装 `IFileContextProvider.GetContextsForFileAsync`
    - 新しい`FileContext`で、`contextType`として一意に生成されたコンス トラクターの引数 `Guid`
    - 使用して、`Context`のプロパティ、`FileContext`する追加のデータを提供する、 `ILanguageServiceProvider`
- 言語サービス
  - プロバイダー ファクトリ
    - `ExportLanguageServiceProvider` 上記の属性が生成される一意`Guid`で `SupportedContextTypes`
    - 実装 `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - プロバイダー
    - 実装 `ILanguageServiceProvider`
    - 使用`ILanguageServiceProvider.InitializeAsync`ファイルを開くときに指定された引数の言語サービスを有効にするには
    - 使用`ILanguageServiceProvider.UninitializeAsync`ファイルが閉じられたときに指定された引数の言語サービスを無効にするには

>[!WARNING]
>`ILanguageServiceProvider`メソッドは、メイン スレッドで、ワークスペースによって呼び出される可能性があります。 UI の遅延の概要を回避するために別のスレッドで作業をスケジュール設定を検討してください。

## <a name="language-server-protocol"></a>言語サーバー プロトコル

`Microsoft.VisualStudio.Workspace.*` Api が開いているフォルダーに、言語サービスを有効にする唯一の方法はありません。 別のオプションでは、言語のサーバーを使用します。 詳細については、「、[言語サーバー プロトコル](language-server-protocol.md)します。

## <a name="related-interfaces"></a>関連するインターフェイス

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> 一致するファイルの種類のファイルを開いたり、編集の終了時に呼び出されます。

## <a name="next-steps"></a>次の手順

* [ワークスペース ビルド](workspace-build.md)-フォルダーを開くサポートは、MSBuild とメイクファイルなどのシステムを構築します。 