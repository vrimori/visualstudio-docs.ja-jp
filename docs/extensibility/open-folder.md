---
title: Visual Studio フォルダーを開く機能拡張の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d916ea30dd9b72a2d8bd59e8d3d34f9e73c74877
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138985"
---
# <a name="open-folder-extensibility"></a>開いているフォルダーの機能拡張

[フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)機能により、ユーザーを開くには Visual Studio でソリューションまたはプロジェクト ファイルがなくても codebase いずれか。 開いているフォルダーは、機能のユーザーがなど Visual Studio から得られるが提供します。

* ソリューション エクスプ ローラーの統合と検索
* エディターの色づけ
* ナビゲーションを参照してください。
* ファイルの検索で検索します。

.NET および C++ の開発などのワークロードに使用する場合のユーザーも得られます。

* リッチ Intellisense
* 言語固有の機能

フォルダーを開くには、拡張機能の作成者は任意の言語の豊富な機能を作成できます。 ユーザーのすべてのファイルのコードベースのビルド、デバッグ、およびシンボルの検索をサポートするための Api があります。 現在エクステンダーは、既存のプロジェクトまたはソリューションからの支援なしのコードを理解する Visual Studio の機能を更新できます。

## <a name="an-api-without-project-systems"></a>プロジェクト システムなしの API

従来は、Visual Studio は、ソリューションとプロジェクト システムを使用して、プロジェクト内のファイルのみを認識します。 プロジェクト システムは、読み込まれたプロジェクトの機能やユーザーの相互作用を担当します。 これには、そのプロジェクト ファイルが含まれているプロジェクトの内容を他のプロジェクトへの依存関係のビジュアル表現され、基になる変更、プロジェクト ファイルが認識しています。 これらの階層およびその他のコンポーネントは、ユーザーの代理として機能する機能を勧めします。 コードベースすべては、プロジェクトとソリューションの構造にも表されます。 スクリプト言語および Linux 用 C++ で記述されたオープン ソース コードは、良い例です。 フォルダーを開くには、Visual Studio は、ユーザーがソース コードとの対話の新しい方法を表示します。

開いているフォルダーの Api が下にある、`Microsoft.VisualStudio.Workspace.*`名前空間エクステンダーを作成し、データまたは開いているフォルダー内のファイルの周囲のアクションを使用するがあるとします。 拡張機能は、これらの Api を使用して、、多くの領域の機能を提供できます。

- [ワークスペース](workspaces.md)- ワークスペースとその Api は、開いているフォルダーのポイントの機能拡張を開始します。
- [ファイルのコンテキストとアクション](workspace-file-contexts.md)-ファイルの特定のコード インテリジェンス ファイル コンテキストを通じて提供します。
- [インデックス作成](workspace-indexing.md)- を収集し、開いているフォルダーのワークスペースに関するデータを保持します。
- [言語サービス](workspace-language-services.md)-言語サービスを開いているフォルダーのワークスペースに統合します。
- [ビルド](workspace-build.md)-フォルダーを開くワークスペースのサポートを構築します。

次の種類を使用する機能は、開いているフォルダーをサポートするために新しい Api を採用する必要があります。

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>フィードバックについては、コメント、問題

フォルダーを開き、 `Microsoft.VisualStudio.Workspace.*` Api は、アクティブな開発でします。 予期しない動作を表示する場合は、目的のリリースの既知の問題を参照してください。 開発者コミュニティとは、投票をすべての問題を作成する推奨される場所です。 フィードバックについては、各を強くお勧め、問題の詳細な説明。 Visual Studio のバージョンを開発している、(実装するものと対話する新機能の両方) を使用している Api、予想される結果と実際の結果が含まれます。 可能であれば、devenv.exe プロセスのダンプが含まれます。 GitHub の問題についてフィードバックの提供の追跡を使用し、関連するドキュメントです。

## <a name="next-steps"></a>次の手順

* [ワークスペース](workspaces.md)-フォルダーを開くワークスペース API について説明します。