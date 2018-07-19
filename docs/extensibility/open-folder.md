---
title: Visual Studio フォルダーを開く機能拡張の概要 |Microsoft Docs
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
ms.openlocfilehash: dcb2d1d922b4ebd4943c42c478400c5873af9cc4
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302977"
---
# <a name="open-folder-extensibility"></a>拡張機能のフォルダーを開く

[フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)機能により、ユーザーを開く Visual Studio でソリューションまたはプロジェクト ファイルを必要としない任意のコードベースです。 開いているフォルダーでは、Visual Studio からなどの機能のユーザーが期待を提供します。

* ソリューション エクスプ ローラーの統合と検索
* エディターの色づけ
* 移動するナビゲーション
* ファイルの検索で検索します。

.NET および C++ の開発などのワークロードを併用すると、ユーザーも取得します。

* 豊富な Intellisense
* 言語固有の機能

フォルダーを開くには、拡張機能の作成者は任意の言語の豊富な機能を作成できます。 ユーザーのすべてのファイルのコードベースのビルド、デバッグ、およびシンボルの検索をサポートする Api があります。 現在のエクステンダーには、プロジェクトまたはソリューションからの支援なしのコードを理解する既存の Visual Studio の機能を更新できます。

## <a name="an-api-without-project-systems"></a>プロジェクト システムなしの API

従来は、Visual Studio は、ソリューションとプロジェクト システムを使用してそのプロジェクト内のファイルのみを認識します。 プロジェクト システムは、読み込まれたプロジェクトの機能とユーザーの相互作用を担当します。 そのプロジェクト ファイルが含まれているプロジェクトの内容、その他のプロジェクトでは、依存関係の視覚表示され、基になる変更、プロジェクト ファイルを認識します。 これらの階層およびその他のコンポーネントは、ユーザーの代理として動作する機能を経由します。 コードベースすべてではなく、プロジェクトとソリューションの構造体で表されます。 スクリプト言語および Linux 用、C++ で記述されたオープン ソース コードは、適切な例を示します。 フォルダーを開くには、Visual Studio のソース コードと対話する新しい方法をユーザーに提供します。

オープン フォルダー Api は、`Microsoft.VisualStudio.Workspace.*`名前空間られ、エクステンダーを作成し、データまたは開いているフォルダー内のファイルのアクションを使用するのに使用できます。 拡張機能は、これらの Api を使用して、、多くの領域の機能を提供できます。

- [ワークスペース](workspaces.md)- ワークスペースとその Api は、フォルダーを開くのポイントの機能拡張を開始します。
- [ファイルのコンテキストとアクション](workspace-file-contexts.md)-ファイルのコンテキストによって提供される特定のコードのインテリジェンスをファイルします。
- [インデックス作成](workspace-indexing.md)- 収集し、フォルダーを開くワークスペースに関するデータを保持します。
- [言語サービス](workspace-language-services.md)-フォルダーを開くのワークスペースに言語サービスを統合します。
- [ビルド](workspace-build.md)-ワークスペースの フォルダーを開くサポートを構築します。

次の型を使用する機能は、開いているフォルダーをサポートするために新しい Api を採用する必要があります。

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>フィードバック、コメント、問題

フォルダーを開くと、 `Microsoft.VisualStudio.Workspace.*` Api は、アクティブな開発。 予期しない動作を表示する場合は、目的のリリースの既知の問題を参照してください。 [開発者コミュニティ](https://developercommunity.visualstudio.com)は投票し、問題を作成する推奨される場所です。 各フィードバックについては、強くお勧め、問題の詳細な説明。 Visual Studio のバージョンを開発している、(実装したし、対話しているもの) を使用している Api、予想される結果、および実際の結果が含まれます。 可能であれば、devenv.exe プロセスのダンプが含まれます。 GitHub の問題の追跡についてフィードバックを使用し、関連するドキュメント。

## <a name="next-steps"></a>次の手順

* [ワークスペース](workspaces.md)-フォルダーを開くワークスペース API について説明します。