---
title: コマンド ライン パラメーターを使用して Visual Studio をインストールする
titleSuffix: ''
description: コマンド ライン パラメーターを使用して、Visual Studio のインストールを制御またはカスタマイズする方法を説明します。
ms.date: 11/14/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a83b3c1be5beeeb2ea40fb9d27089a4b559f758a
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55089143"
---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする

コマンド プロンプトから Visual Studio 2017 をインストールする場合、さまざまなコマンド ライン パラメーターを使用してインストールを管理またはカスタマイズすることができます。 コマンド ラインから、次の操作を行うことができます。

- 特定のオプションをあらかじめ選択してインストールする。
- インストール プロセスを自動化する。
- 後で使用できるようにインストール ファイルのキャッシュ (レイアウト) を作成する。

コマンド ライン オプションは、セットアップ ブートストラップという、ダウンロード プロセスを開始する約 1 MB の小さなファイルと組み合わせて使用されます。 ブートストラップは、Visual Studio サイトからダウンロードしたときに起動される最初の実行可能ファイルです。 次のリンクから、インストールする製品エディションに応じた最新リリースのブートストラップを直接取得できます。

- [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)

## <a name="command-line-parameters"></a>コマンド ライン パラメーター

 Visual Studio のコマンド ライン パラメーターでは、大文字と小文字は区別されません。

> 構文: `vs_enterprise.exe [command] <options>...`

(`vs_enterprise.exe` は、インストールする製品エディションに適宜置き換えてください。)

>[!TIP]
> コマンドラインを使用して Visual Studio 2017 をインストールする方法の他の例については、[コマンド ライン パラメーターの例](command-line-parameter-examples.md)に関するページをご覧ください。

| **コマンド** | **説明** |
| ----------------------- | --------------- |
| (空白) | 製品をインストールします。 |
| `modify` | インストールされている製品を変更します。 |
| `update` | インストールされている製品を更新します。 |
| `repair` | インストールされている製品を修復します。 |
| `uninstall` | インストールされている製品をアンインストールします。 |
| `export` | **15.9 の新機能**:インストールの選択をインストール構成ファイルにエクスポートします。 **注**:vs_installer.exe でのみ使用できます。 |

## <a name="install-options"></a>インストール オプション

| **インストール オプション** | **説明** |
| ----------------------- | --------------- |
| `--installPath <dir>` | 操作するインスタンスのインストール ディレクトリです。 インストール コマンドの場合、これは**省略可能**で、インスタンスがインストールされる場所になります。 その他のコマンドではこれは**必須**で、以前にインストール済みのインスタンスがインストールされた場所になります。 |
| `--addProductLang <language-locale>` | **省略可能**:インストールまたは変更操作時に、製品にインストールされる UI 言語パックを決定します。 コマンド ラインに複数回指定して複数の言語パックを追加できます。 指定しない場合、インストール時にはコンピューターのロケールが使用されます。 詳しくは、このページの「[言語ロケールの一覧](#list-of-language-locales)」セクションをご覧ください。|
| `--removeProductLang <language-locale>` | **省略可能**:インストールまたは変更操作時に、製品から削除される UI 言語パックを決定します。 コマンド ラインに複数回指定して複数の言語パックを追加できます。 詳しくは、このページの「[言語ロケールの一覧](#list-of-language-locales)」セクションをご覧ください。|
| `--add <one or more workload or component IDs>` | **省略可能**:1 つ以上のワークロード ID またはコンポーネント ID を追加します。 成果物の必須のコンポーネントはインストールされますが、推奨されるコンポーネントまたは省略可能なコンポーネントはインストールされません。 `--includeRecommended` や `--includeOptional` を使用して、他のコンポーネントをグローバルに制御できます。 複数のワークロードやコンポーネントを含める場合、`--add` コマンドを繰り返します (例: `--add Workload1 --add Workload2`)。 詳細に制御するために、ID に `;includeRecommended` または `;includeOptional` を追加できます (例: `--add Workload1;includeRecommended` または `--add Workload2;includeRecommended;includeOptional`)。 詳しくは、[ワークロード ID とコンポーネント ID](workload-and-component-ids.md) に関するページをご覧ください。 必要に応じて、このオプションを繰り返すことができます。|
| `--remove <one or more workload or component IDs>` | **省略可能**:1 つ以上のワークロード ID またはコンポーネント ID を削除します。 詳しくは、[ワークロード ID とコンポーネント ID](workload-and-component-ids.md) に関するページをご覧ください。 必要に応じて、このオプションを繰り返すことができます。|
| `--in <path>` | **省略可能**:応答ファイルへの URI またはパスです。  |
| `--all` | **省略可能**:製品のすべてのワークロードおよびコンポーネントをインストールするかどうかを指定します。 |
| `--allWorkloads` | **省略可能**:すべてのワークロードとコンポーネントをインストールし、推奨されるコンポーネントと省略可能なコンポーネントはインストールしません。 |
| `--includeRecommended` | **省略可能**:インストールされているワークロードの推奨されるコンポーネントを含めますが、オプションのコンポーネントは含めません。 ワークロードは、`--allWorkloads` または `--add` のいずれかで指定されます。 |
| `--includeOptional` | **省略可能**:インストールされているワークロードのオプションのコンポーネントを含めますが、推奨されるコンポーネントは含めません。 ワークロードは、`--allWorkloads` または `--add` のいずれかで指定されます。  |
| `--quiet, -q` | **省略可能**:インストールの実行中にユーザー インターフェイスを表示しません。 |
| `--passive, -p` | **省略可能**:ユーザー インターフェイスを表示しますが、ユーザーに対話式操作を要求することはありません。 |
| `--norestart` | **省略可能**:指定した場合、`--passive` または `--quiet` を含むコマンドでは、コンピューターを自動的に再起動することはありません (必要な場合)。  `--passive` または `--quiet` のどちらも指定されていない場合は、無視されます。  |
| `--nickname <name>` | **省略可能**:インストールされている製品に割り当てるニックネームを定義します。 ニックネームは 10 文字を超えることはできません。  |
| `--productKey` | **省略可能**:インストールされる製品に使用するプロダクト キーを定義します。 `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` または `xxxxxxxxxxxxxxxxxxxxxxxxx` のいずれかの形式の英数字 25 文字で構成されます。 |
| `--help, --?, -h, -?` | このページのオフライン バージョンを表示します。 |
| `--config <path>` | **省略可能**および **15.9 の新機能**:インストールまたは変更の操作中に、以前に保存したインストール構成ファイルに基づいて、追加するワークロードおよびコンポーネントを決定します。 この操作は追加式で、ワークロードやコンポーネントがファイル内に存在しない場合、削除されることはありません。 また、製品に適用されない項目は追加されません。 エクスポート操作中に、インストール構成ファイルの保存場所を決定します。 |

> [!IMPORTANT]
> 複数のワークロードとコンポーネントを指定する場合、項目ごとに `--add` または `--remove` コマンド ライン スイッチを繰り返す必要があります。

## <a name="layout-options"></a>レイアウト オプション

| **レイアウト オプション** | **説明** |
| ----------------------- | --------------- |
| `--layout <dir>` | オフライン インストールのキャッシュを作成するディレクトリを指定します。 詳細については、「[Visual Studio のネットワーク ベース インストールを作成する](create-a-network-installation-of-visual-studio.md)」をご覧ください。|
| `--lang <one or more language-locales>` | **省略可能**:`--layout` とともに使用して、指定した言語でのリソース パッケージによるオフライン インストール キャッシュを準備します。 詳しくは、このページの「[言語ロケールの一覧](#list-of-language-locales)」セクションをご覧ください。|
| `--add <one or more workload or component IDs>` | **省略可能**:1 つ以上のワークロード ID またはコンポーネント ID を追加します。 成果物の必須のコンポーネントはインストールされますが、推奨されるコンポーネントまたは省略可能なコンポーネントはインストールされません。 `--includeRecommended` や `--includeOptional` を使用して、他のコンポーネントをグローバルに制御できます。 詳細に制御するために、ID に `;includeRecommended` または `;includeOptional` を追加できます (例: `--add Workload1;includeRecommended` または `--add Workload2;includeOptional`)。 詳しくは、[ワークロード ID とコンポーネント ID](workload-and-component-ids.md) に関するページをご覧ください。 <br/>**注**:`--add` を使用する場合、指定したワークロードとコンポーネント、およびその依存関係のみがダウンロードされます。 `--add` を指定しない場合は、すべてのワークロードとコンポーネントがレイアウトにダウンロードされます。|
| `--includeRecommended` | **省略可能**:インストールされているワークロードの推奨されるコンポーネントを含めますが、オプションのコンポーネントは含めません。 ワークロードは、`--allWorkloads` または `--add` のいずれかで指定されます。 |
| `--includeOptional` | **省略可能**:レイアウトに含まれるワークロードに、推奨*および*省略可能なコンポーネントが含まれます。 ワークロードは、`--add` で指定されます。  |
| `--keepLayoutVersion` | **15.3 の新機能、省略可能**:レイアウトのバージョンを更新することなく、レイアウトに変更を適用します。 |
| `--verify` | **15.3 の新機能、省略可能**:レイアウトの内容を確認します。 破損または欠落しているすべてのファイルが一覧に表示されます。 |
| `--fix` | **15.3 の新機能、省略可能**:レイアウトの内容を確認します。  破損または欠落しているファイルが見つかった場合は、再ダウンロードします。 レイアウトを修正するには、インターネットへのアクセスが必要です。 |
| `--clean <one or more paths to catalogs>` | **15.3 の新機能、省略可能**:新しいバージョンに更新されたレイアウトから古いバージョンのコンポーネントを削除します。 |

| **高度なインストール オプション** | **説明** |
| ----------------------- | --------------- |
| `--channelId <id>` | **省略可能**:インストールするインスタンスのチャネル ID です。 インストール コマンドでは必須です。`--installPath` を指定した場合、その他のコマンドは無視されます。 |
| `--channelUri <uri>` | **省略可能**:チャネル マニフェストの URI です。 更新が望ましくない場合は、`--channelUri` で存在しないファイルを指定できます  (例: --channelUri C:\doesntExist.chman)。これはインストール コマンドに使用できます。その他のコマンドでは無視されます。 |
| `--installChannelUri <uri>` | **省略可能**:インストールに使用するチャネル マニフェストの URI です。 `--channelUri` で指定された URI (`--installChannelUri` を指定した場合は必ず指定する必要があります) は、更新プログラムを検出するために使用されます。 インストール コマンドに使用できます。その他のコマンドでは無視されます。 |
| `--installCatalogUri <uri>` | **省略可能**:インストールに使用するカタログ マニフェストの URI です。 これを指定すると、チャネル マネージャーは、インストール チャネル マニフェストの URI を使用する前に、この URI からカタログ マニフェストをダウンロードしようとします。 このパラメーターは、レイアウトのキャッシュが既にダウンロードされている製品カタログで作成される、オフライン インストールをサポートするために使用されます。 インストール コマンドに使用できます。その他のコマンドでは無視されます。 |
| `--productId <id>` | **省略可能**: インストールされるインスタンスの製品 ID です。 これは、通常のインストールの条件下では事前に配布されています。 |
| `--wait` | **省略可能**:インストールが完了し、終了コードが返されるまでプロセスは待機します。 このオプションは、インストールが完了するまで待ってから、そのインストールからのリターン コードを処理する必要があるインストールの自動化に役立ちます。 |
| `--locale <language-locale>` | **省略可能**:インストーラー自体のユーザー インターフェイスの表示言語を変更します。 設定は保持されます。 詳しくは、このページの「[言語ロケールの一覧](#list-of-language-locales)」セクションをご覧ください。|
| `--cache` | **15.2 の新機能、省略可能**:指定した場合、インストールされた後、その後の修復用にパッケージが保持されます。 このオプションでは、その後のインストール、修復、または修正に使用されるグローバル ポリシー設定がオーバーライドされます。 既定のポリシーでは、パッケージをキャッシュします。 アンインストール コマンドでは、これは無視されます。 詳細については、「[disable or move the package cache](disable-or-move-the-package-cache.md)」 (パッケージ キャッシュの無効化または移動) を参照してください。 |
| `--nocache` | **15.2 の新機能、省略可能**:指定した場合、パッケージはインストールまたは修復された後、削除されます。 必要な場合にのみ、もう一度ダウンロードされ、使用後はもう一度削除されます。 このオプションでは、その後のインストール、修復、または修正に使用されるグローバル ポリシー設定がオーバーライドされます。 既定のポリシーでは、パッケージをキャッシュします。 アンインストール コマンドでは、これは無視されます。 詳細については、「[disable or move the package cache](disable-or-move-the-package-cache.md)」 (パッケージ キャッシュの無効化または移動) を参照してください。 |
| `--noUpdateInstaller` | **15.2 の新機能、省略可能**:指定した場合、quiet が指定されていると、インストーラーはインストーラー自体を更新しません。 インストーラーの更新が必要な場合に、noUpdateInstaller と quiet の両方が指定されていると、インストーラーはコマンドを失敗させて、0 以外の終了コードを返します。 |
| `--noWeb` | **15.3 の新機能、省略可能**:インターネットからインストールしているコンテンツのダウンロードが即時セットアップされます。  インストールされるすべてのコンテンツがオフライン レイアウトで使用できる必要があります。  レイアウトにコンテンツがない場合、セットアップは失敗します。  詳細については、「[ネットワーク インストールから展開する](create-a-network-installation-of-visual-studio.md)」をご覧ください。 |
| `--path <name>=<path>` | **15.7 の新機能、省略可能**:インストール用のカスタム インストール パスを指定するために使用します。 サポートされているパス名は、shared、cache、および install です。 |
| `--path cache=<path>` | **15.7 の新機能、省略可能**:指定した場所を使用してインストール ファイルをダウンロードします。 この場所は、Visual Studio を初めてインストールするときにのみ設定することができます。 例 : `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **15.7 の新機能、省略可能**:Visual Studio のサイド バイ サイド インストール用の共有ファイルが含まれています。 ツールおよび SDK については、このドライブ上の場所にインストールされるものもあれば、この設定をオーバーライドして、別のドライブにインストールされるものもあります。 例 : `--path shared="C:\VS\shared"` <br><br>重要 : これは Visual Studio を初めてインストールするときに 1 回のみ設定できます。 |
| `--path install=<path>` | **15.7 の新機能、省略可能**:これは、`–-installPath` に相当します。 具体的には、`--installPath "C:\VS"` と `--path install="C:\VS"` が等価です。 これらは、一度に 1 つずつしか使用できません。 |

## <a name="list-of-workload-ids-and-component-ids"></a>ワークロード ID とコンポーネント ID の一覧

Visual Studio 製品ごとに並べられているワークロード ID とコンポーネント ID の一覧については、「[Visual Studio 2017 のワークロード ID とコンポーネント ID](workload-and-component-ids.md)」のページを参照してください。

## <a name="list-of-language-locales"></a>言語ロケールの一覧

| **言語ロケール** | **Language** |
| ----------------------- | --------------- |
| Cs-cz | チェコ語 |
| De-de | ドイツ語 |
| En-us | 英語 |
| Es-es | スペイン語 |
| Fr-fr | フランス語 |
| It-it | イタリア語 |
| Ja-jp | 日本語 |
| Ko-kr | 韓国語 |
| Pl-pl | ポーランド語 |
| Pt-br | ポルトガル語 - ブラジル |
| Ru-ru | ロシア語 |
| Tr-tr | トルコ語 |
| Zh-cn | 中国語 - 簡体字 |
| Zh-tw | 中国語 - 繁体字 |

## <a name="error-codes"></a>エラー コード

操作の結果に応じて、`%ERRORLEVEL%` 環境変数は、次のいずれかの値に設定されます。

| **[値]** | **結果** |
| --------- | ---------- |
| 0 | 操作は正常に終了しました |
| 1602 | 操作が取り消されました |
| 3010 | 操作は正常に完了しましたが、インストールした製品を使用する前に再起動が必要です |
| 5004 | 操作が取り消されました |
| 5007 | 操作がブロックされました - コンピューターが要件を満たしていません |
| その他 | 失敗の状態が発生しました。詳細については、ログを参照してください |

操作ごとに、インストールの進行状況を示す複数のログ ファイルが `%TEMP%` ディレクトリに生成されます。 フォルダーを日付で並べ替え、`dd_bootstrapper`、`dd_client`、`dd_setup` で始まるファイルを探します (それぞれブートストラップ、インストーラー アプリ、セットアップ エンジンを表します)。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

- [Visual Studio 2017 のインストールに使用するコマンド ライン パラメーターの例](command-line-parameter-examples.md)
- [Visual Studio 2017 のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
- [応答ファイルで Visual Studio インストールを自動化する](automated-installation-with-response-file.md)
- [Visual Studio 2017 のワークロード ID とコンポーネント ID](workload-and-component-ids.md)