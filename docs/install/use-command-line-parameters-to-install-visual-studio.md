---
title: "コマンド ライン パラメーターを使用して Visual Studio をインストールする | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: b5b496e0de0a12c9f52c944ef9e768c82d9be783
ms.openlocfilehash: 429d55b3d0050eb0743d4abf39c202ad1b8383b1
ms.contentlocale: ja-jp
ms.lasthandoff: 05/08/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする
コマンド プロンプトから Visual Studio 2017 をインストールする場合、さまざまなコマンド ライン パラメーターを使用してインストールを管理またはカスタマイズすることができます。 コマンド ラインから、次の操作を行うことができます。

- 特定のオプションをあらかじめ選択してインストールする。
- インストール プロセスを自動化する。
- 後で使用できるようにインストール ファイルのキャッシュ (レイアウト) を作成する。

コマンド ライン オプションは、セットアップ ブートストラップという、ダウンロード プロセスを開始する約 1 MB の小さなファイルと組み合わせて使用されます。 ブートストラップは、Visual Studio サイトからダウンロードしたときに起動される最初の実行可能ファイルです。 次のリンクから、インストールする製品エディションに応じた最新リリースのブートストラップを直接取得できます。

* [Visual Studio 2017 Enterprise](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio 2017 Professional](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio 2017 Community](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>コマンド ライン パラメーターの一覧  
 Visual Studio のコマンド ライン パラメーターでは、大文字と小文字は区別されません。

> 構文: `vs_enterprise.exe [command] <options>...`

(`vs_enterprise.exe` は、インストールする製品エディションに適宜置き換えてください。 例については、[コマンド ライン パラメーターの例](command-line-parameter-examples.md)のページを参照してください。)

| **コマンド** | **説明** |
| ----------------------- | --------------- |
| (空白) | 製品をインストールします。 |
| `modify` | インストールされている製品を変更します。 |
| `update` | インストールされている製品を更新します。 |
| `repair` | インストールされている製品を修復します。 |
| `uninstall` | インストールされている製品をアンインストールします。 |

| **インストール オプション** | **説明** |
| ----------------------- | --------------- |
| `--installPath <dir>` | 操作するインスタンスのインストール ディレクトリです。 インストール コマンドの場合、これは**省略可能**で、インスタンスがインストールされる場所になります。 その他のコマンドでは、これは**必須**で、以前にインストール済みのインスタンスがインストールされた場所です。 |
| `--addProductLang <language-locale>` | **省略可能**: インストールまたは変更操作時に、製品にインストールされる UI 言語パックを決定します。 コマンド ラインに複数回指定して複数の言語パックを追加できます。 指定しない場合、インストールではコンピューターのロケールが使用されます。 詳しくは、このページの「[言語ロケールの一覧](#list-of-language-locales)」セクションをご覧ください。|
| `--removeProductLang <language-locale>` | **省略可能**: インストールまたは変更操作時に、製品から削除される UI 言語パックを決定します。 コマンド ラインに複数回指定して複数の言語パックを追加できます。 詳しくは、このページの「[言語ロケールの一覧](#list-of-language-locales)」セクションをご覧ください。|
| `--add <one or more workload or component IDs>` | **省略可能**: 1 つ以上のワークロード ID またはコンポーネント ID を追加します。 成果物の必須のコンポーネントはインストールされますが、推奨されるコンポーネントまたは省略可能なコンポーネントはインストールされません。 `--includeRecommended` や `--includeOptional` を使用して、他のコンポーネントをグローバルに制御できます。 詳細に制御するために、ID に `;includeRecommended` または `;includeOptional` を追加できます (例: `--add Workload1;includeRecommended` または `--add Workload2;includeRecommended;includeOptional`)。 詳しくは、[ワークロード ID とコンポーネント ID](workload-and-component-ids.md) に関するページをご覧ください。|
| `--remove <one or more workload or component IDs>` | **省略可能**: 1 つ以上のワークロード ID またはコンポーネント ID を削除します。 詳しくは、[ワークロード ID とコンポーネント ID](workload-and-component-ids.md) に関するページをご覧ください。|
| `--in <path>` | **省略可能**: 応答ファイルへの URI またはパスです。  |
| `--all` | **省略可能**: 製品のすべてのワークロードおよびコンポーネントをインストールするかどうかを指定します。 |
| `--allWorkloads` | **省略可能**: すべてのワークロードとその必須コンポーネントをインストールし、推奨されるコンポーネントと省略可能なコンポーネントはインストールしません。 |
| `--includeRecommended` | **省略可能**: インストールされているワークロードの推奨されるコンポーネントを含めますが、オプションのコンポーネントは含めません。 ワークロードは、`--allWorkloads` または `--add` のいずれかで指定されます。 |
| `--includeOptional` | **省略可能**: インストールされているワークロードのオプションのコンポーネントを含めますが、推奨されるコンポーネントは含めません。 ワークロードは、`--allWorkloads` または `--add` のいずれかで指定されます。  |
| `--quiet, -q` | **省略可能**: インストールの実行中にユーザー インターフェイスを表示しません。 |
| `--passive, -p` | **省略可能**: ユーザー インターフェイスを表示しますが、ユーザーに対話式操作を要求することはありません。 |
| `--norestart` | **省略可能**: 指定した場合、`--passive` または `--quiet` を含むコマンドでは、コンピューターを自動的に再起動することはありません (必要な場合)。 `--passive` または `--quiet` のどちらも指定されていない場合は、無視されます。  |
| `--nickname <name>` | **省略可能**: インストールされている製品に割り当てるニックネームを定義します。 ニックネームは 10 文字を超えることはできません。  |
| `--productKey` | **省略可能**: インストールされる製品に使用するプロダクト キーを定義します。 `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` または `xxxxxxxxxxxxxxxxxxxxxxxxx` のいずれかの形式の英数字 25 文字で構成されます。 |
| `--help, --?, -h, -?` | このページのオフライン バージョンを表示します。 |

> 注: 複数のワークロードとコンポーネントを指定する場合、項目ごとに `--add` または `--remove` コマンド ライン スイッチを繰り返す必要があります。

| **レイアウト オプション** | **説明** |
| ----------------------- | --------------- |
| `--layout <dir>` | オフライン インストールのキャッシュを作成するディレクトリを指定します。 詳細については、「[Visual Studio のネットワーク ベース インストールを作成する](create-a-network-installation-of-visual-studio.md)」を参照してください。|
| `--lang <one or more language-locales>` | **省略可能**: `--layout` とともに使用して、指定した言語でのリソース パッケージによるオフライン インストール キャッシュを準備します。 詳しくは、このページの「[言語ロケールの一覧](#list-of-language-locales)」セクションをご覧ください。|
| `--add <one or more workload or component IDs>` | **省略可能**: 1 つ以上のワークロード ID またはコンポーネント ID を追加します。 成果物の必須のコンポーネントはインストールされますが、推奨されるコンポーネントまたは省略可能なコンポーネントはインストールされません。 `--includeRecommended` や `--includeOptional` を使用して、他のコンポーネントをグローバルに制御できます。 詳細に制御するために、ID に `;includeRecommended` または `;includeOptional` を追加できます (例: `--add Workload1;includeRecommended` または `--add Workload2;includeOptional`)。 詳しくは、[ワークロード ID とコンポーネント ID](workload-and-component-ids.md) に関するページをご覧ください。 <br/>**注意**: `--add` を使用する場合、指定したワークロードとコンポーネント、およびその依存関係のみがダウンロードされます。 `--add` が指定されない場合は、すべてのワークロードとコンポーネントがレイアウトにダウンロードされます。|
| `--includeRecommended` | **省略可能**: インストールされているワークロードの推奨されるコンポーネントを含めますが、オプションのコンポーネントは含めません。 ワークロードは、`--allWorkloads` または `--add` のいずれかで指定されます。 |
| `--includeOptional` | **省略可能**: レイアウトに含まれるワークロードに、推奨*および*省略可能なコンポーネントが含まれます。 ワークロードは、`--add` で指定されます。  |


| **高度なインストール オプション** | **説明** |
| ----------------------- | --------------- |
| `--channelId <id>` | **省略可能**: インストールするインスタンスのチャネル ID です。 インストール コマンドでは必須です。`--installPath` を指定した場合、その他のコマンドは無視されます。 |
| `--channelUri <uri>` | **省略可能**: チャネル マニフェストの URI です。 インストール コマンドに使用できます。その他のコマンドでは無視されます。 |
| `--installChannelUri <uri>` | **省略可能**: インストールに使用するチャネル マニフェストの URI です。 `--channelUri` (`--installChannelUri` を指定した場合は、必ず指定する必要があります) で指定された URI は、更新プログラムを検出するために使用されます。 更新プログラムが必要でない場合は、引数なしで `--channelUri` を指定する必要があります。 インストール コマンドに使用できます。その他のコマンドでは無視されます。 |
| `--installCatalogUri <uri>` | **省略可能**: インストールに使用するカタログ マニフェストの URI です。 指定すると、チャネル マネージャーは、インストール チャネル マニフェストの URI を使用する前に、この URI からカタログ マニフェストをダウンロードしようとします。 このパラメーターは、レイアウトのキャッシュが既にダウンロードされている製品カタログで作成される、オフライン インストールをサポートするために使用されます。 インストール コマンドに使用できます。その他のコマンドでは無視されます。 |
| `--productId <id>` | **省略可能**: インストールされるインスタンスの製品 ID です。 これは、通常のインストールの条件下では事前に配布されています。 |
| `--wait` | **省略可能**: プロセスは終了コードを返す前に、インストールが完了するまで待機します。 このオプションは、インストールが完了するまで待ってから、そのインストールからのリターン コードを処理する必要があるインストールの自動化に役立ちます。 |
| `--locale <language-locale>` | **省略可能**: インストーラー自体のユーザー インターフェイスの表示言語を変更します。 設定は保持されます。 詳しくは、このページの「[言語ロケールの一覧](#list-of-language-locales)」セクションをご覧ください。|
| `--cache` | **15.2 の新機能、省略可能**: 指定した場合、インストールされた後、その後の修復用にパッケージが保持されます。 このオプションでは、その後のインストール、修復、または修正に使用されるグローバル ポリシー設定がオーバーライドされます。 既定のポリシーでは、パッケージをキャッシュします。 アンインストール コマンドでは、これは無視されます。 詳細については、「[disable or move the package cache](disable-or-move-the-package-cache.md)」 (パッケージ キャッシュの無効化または移動) を参照してください。 |
| `--nocache` | **15.2 の新機能、省略可能**: 指定した場合、インストールまたは修復された後に、パッケージが削除されます。 必要な場合にのみ、もう一度ダウンロードされ、使用後はもう一度削除されます。 このオプションでは、その後のインストール、修復、または修正に使用されるグローバル ポリシー設定がオーバーライドされます。 既定のポリシーでは、パッケージをキャッシュします。 アンインストール コマンドでは、これは無視されます。 詳細については、「[disable or move the package cache](disable-or-move-the-package-cache.md)」 (パッケージ キャッシュの無効化または移動) を参照してください。 |

## <a name="list-of-workload-ids-and-component-ids"></a>ワークロード ID とコンポーネント ID の一覧
Visual Studio 製品ごとに並べられているワークロード ID とコンポーネント ID の一覧については、「[Visual Studio 2017 のワークロード ID とコンポーネント ID](workload-and-component-ids.md)」のページを参照してください。

## <a name="list-of-language-locales"></a>言語ロケールの一覧
| **言語ロケール** | **言語** |
| ----------------------- | --------------- |
| cs-CZ | チェコ語 |
| de-DE | ドイツ語 |
| en-US | 英語 |
| es-ES | スペイン語 |
| fr-FR | フランス語 |
| it-IT | イタリア語 |
| ja-JP | 日本語 |
| ko-KR | 韓国語 |
| pl-PL | ポーランド語 |
| pt-BR | ポルトガル語 - ブラジル |
| ru-RU | ロシア語 |
| tr-TR | トルコ語 |
| zh-CN | 中国語 - 簡体字 |
| zh-TW | 中国語 - 繁体字 |

## <a name="error-codes"></a>エラー コード
操作の結果に応じて、`%ERRORLEVEL%` 環境変数は、次のいずれかの値に設定されます。

| **値** | **結果** |
| --------- | ---------- |
| 0 | 操作は正常に終了しました |
| 3010 | 操作は正常に完了しましたが、インストールした製品を使用する前に再起動が必要です |
| その他 | 失敗の状態が発生しました。詳細については、ログを参照してください |

操作ごとにインストールの進行状況を示す複数のログ ファイルが `%TEMP%` ディレクトリに生成されます。 フォルダーを日付で並べ替え、`dd_bootstrapper`、`dd_client`、`dd_setup` で始まるファイルを探します (それぞれブートストラップ、インストーラー アプリ、セットアップ エンジンを表します)。

## <a name="see-also"></a>関連項目

 * [Visual Studio 2017 のインストール](install-visual-studio.md)
 * [Visual Studio 2017 のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
 * [Visual Studio 2017 のインストールに使用するコマンド ライン パラメーターの例](command-line-parameter-examples.md)
 * [応答ファイルで Visual Studio インストールを自動化する](automated-installation-with-response-file.md)
 * [Visual Studio 2017 で問題を報告する](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

