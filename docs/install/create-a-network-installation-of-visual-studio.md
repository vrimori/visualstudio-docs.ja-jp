---
title: "Visual Studio のネットワーク ベース インストールを作成する | Microsoft Docs"
description: "企業内に Visual Studio を展開するためのネットワーク インストール ポイントを作成する方法について説明します"
ms.date: 10/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: timsneath
ms.author: tglee
manager: ghogen
ms.openlocfilehash: fa4aec5f164e188ff9832d06a4b3c8dad46ae63d
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2017
---
# <a name="create-a-network-installation-of-visual-studio-2017"></a>Visual Studio 2017 のネットワーク インストールを作成する

一般的に、企業の管理者はクライアント ワークステーションに展開するためのネットワーク インストール ポイントを作成します。 Visual Studio 2017 は、初期インストールのファイルがすべての製品の更新プログラムとともに単一のファイルにキャッシュできるように設計されています。 (このプロセスは_レイアウトの作成_とも呼ばれています。)これは、最新のサービスの更新プログラムに更新されていない場合でも、クライアント ワークステーションが同じネットワークの場所を使用してインストールを管理できるようにするためです。

> [!NOTE]
> 複数のエディションの Visual Studio を企業内で利用している場合 (たとえば、Visual Studio Professional と Visual Studio Enterprise の両方)、エディションごとに個別のネットワーク インストール共有を作成する必要があります。

## <a name="download-the-visual-studio-bootstrapper"></a>Visual Studio ブートストラップをダウンロードする

必要な Visual Studio のエディションを**ダウンロード**します。 必ず **[保存]** をクリックし、**[フォルダーを開く]** をクリックします。

セットアップ実行可能ファイル&mdash;具体的にはブートストラップ ファイル&mdash;は、次のいずれかになります。

|エディション | ダウンロード|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://aka.ms/vs/15/release/vs_enterprise.exe) |
|Visual Studio Professional | [**vs_professional.exe**](https://aka.ms/vs/15/release/vs_professional.exe) |
|Visual Studio コミュニティ | [**vs_community.exe**](https://aka.ms/vs/15/release/vs_community.exe) |

その他にサポートされているブートストラップとして、[vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe)、[vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe)、[vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe)、[vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe)、[vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe)、[vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe) が含まれます。

## <a name="create-an-offline-installation-folder"></a>オフライン インストール フォルダーを作成する

このステップを実行するにはインターネット接続が必要です。 すべての言語およびすべての機能を持つオフライン インストールを作成するには、次の例のいずれかのコマンドを使用します。

   > [!IMPORTANT]
   > Visual Studio 2017 の完全なレイアウトでは、少なくとも 35 GB のディスク領域が必要で、ある程度ダウンロードに時間がかかります。  インストールするコンポーネントのみでレイアウトを作成する方法の詳細については、「[ネットワーク レイアウトをカスタマイズする](#customizing-the-network-layout)」セクションをご覧ください。

   > [!TIP]
   > コマンドをダウンロード ディレクトリから実行していることを確認してください。 通常は、Windows 10 を実行するコンピューター上の `C:\Users\<username>\Downloads` です。

- Visual Studio Enterprise の場合、以下を実行します。

  ```vs_enterprise.exe --layout c:\vs2017offline```

- Visual Studio Professional の場合、以下を実行します。

  ```vs_professional.exe --layout c:\vs2017offline```

- Visual Studio コミュニティの場合、以下を実行します。

  ```vs_community.exe --layout c:\vs2017offline```

## <a name="modify-the-responsejson-file"></a>response.json file を変更する

response.json を変更し、セットアップの実行時に使用される既定値を設定できます。  たとえば、特定のワークロード セットが自動的に選択されるように `response.json` ファイルを構成できます。
詳細については、「[Automate Visual Studio installation with a response file](automated-installation-with-response-file.md)」 (応答ファイルで Visual Studio インストールを自動化する) を参照してください。

## <a name="copy-the-layout-to-a-network-share"></a>ネットワーク共有にレイアウトをコピーする

他のコンピューターから実行できるようにネットワーク共有でレイアウトをホストします。
* 例:<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```

## <a name="customizing-the-network-layout"></a>ネットワーク レイアウトをカスタマイズする

ネットワーク レイアウトはいくつかの方法でカスタマイズできます。 [言語ロケール](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)、[ワークロード、コンポーネント、推奨の依存関係または任意の依存関係](workload-and-component-ids.md)からなる特定のセットのみを含む部分的レイアウトを作成できます。 これは、一部のワークロードだけをクライアント ワークステーションに展開することがわかっている場合に便利です。 レイアウトをカスタマイズするための一般的なコマンド ライン パラメーターには次のようなものがあります。

* ```--add``` は[ワークロードまたはコンポーネント ID](workload-and-component-ids.md) を指定します。  `--add` を使用すると、`--add` で指定されたワークロードとコンポーネントだけがダウンロードされます。  `--add` を使用しない場合、すべてのワークロードとコンポーネントがダウンロードされます。
* ```--includeRecommended``` は指定したワークロード ID のすべての推奨コンポーネントを含めます。
* ```--includeOptional``` は指定したワークロード ID のすべての推奨コンポーネントと任意コンポーネントを含めます。
* ```--lang``` は[言語ロケール](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)を指定します。

次に、レイアウトを部分的にカスタマイズする例をいくつか紹介します。

* 1 つの言語に対して、すべてのワークロードとコンポーネントをダウンロードするには、以下を実行します。 <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
* 複数の言語に対して、すべてのワークロードとコンポーネントをダウンロードするには、以下を実行します。 <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
* すべての言語に対して、1 つのワークロードをダウンロードするには、以下を実行します。 <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
* 3 つの言語に対して、2 つのワークロードと 1 つのオプション コンポーネントをダウンロードするには、以下を実行します。 <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
* 2 つのワークロードとその推奨コンポーネントのすべてをダウンロードするには、次を実行します。 <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
* 2 つのワークロードとそのすべての推奨コンポーネントと任意コンポーネントをダウンロードするには、次を実行します。 <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```

### <a name="new-in-153"></a>15.3 の新機能

レイアウト コマンドを実行すると、(ワークロードや言語などの) 指定したオプションが保存されます。 後続のレイアウトコマンドには、それ以前のすべてのオプションが含まれます。  英語のみ対象の 1 つのワークロードを含むレイアウトの例を示します。

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US```

レイアウトを新しいバージョンに更新したい場合、追加のコマンド ライン パラメーターを指定する必要はありません。 このレイアウト フォルダーに保存されている以前の設定が、後続のすべてのレイアウト コマンドで使用されます。  次のコマンドは、既存の部分的レイアウトを更新します。

```vs_enterprise.exe --layout c:\VS2017Layout```

追加のワークロードを追加したい場合は、次のようなコマンドを使用します。 この場合、Azure のワークロードとローカライズされた言語を追加します。  これで、Managed Desktop と Azure の両方がこのレイアウトに含まれるようになります。  英語とドイツ語の言語リソースがすべてのワークロードに含まれます。 レイアウトは利用可能な最新バージョンに更新されます。

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE```

既存のレイアウトを完全なレイアウトに更新したい場合は、次の例に示すように all オプションを使用します。

```vs_enterprise.exe --layout c:\VS2017Layout --all```


## <a name="deploying-from-a-network-installation"></a>ネットワーク インストールから展開する

管理者はインストール スクリプトの一部として Visual Studio をクライアント ワークステーションに展開することができます。 あるいは、管理者権限を持つユーザーは共有から直接セットアップを実行し、自分のコンピューターに Visual Studio をインストールできます。

- ユーザーは次を実行してインストールできます。 <br>```\\server\products\VS2017\vs_enterprise.exe```
- 管理者は次を実行し、無人モードでインストールできます。 <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> バッチ ファイルの一部として実行するとき、`--wait` オプションを利用すると、`vs_enterprise.exe` プロセスはインストールの完了を待ち、それから終了コードを返します。 これは、企業の管理者が完了したインストールに追加のアクション (たとえば、[成功したインストールにプロダクト キーを適用する](automatically-apply-product-keys-when-deploying-visual-studio.md)など) を実行したい場合に便利ですが、そのインストールからのリターン コードを処理するにはインストールが終了するまで待つ必要があります。  `--wait` を使用しない場合、インストールが完了する前に `vs_enterprise.exe` プロセスが終了し、インストール操作の状態を表していない不正確な終了コードが返されます。

レイアウトからインストールする場合、インストールされる内容はレイアウトから取得されます。 ただし、レイアウトに含まれないコンポーネントを選択した場合は、インターネットから取得されます。  Visual Studio のセットアップでレイアウトにない内容がダウンロードされないようにするには、`--noWeb` オプションを使用します。  `--noWeb` が使用されていて、インストール対象として選択されている内容がレイアウトにない場合、セットアップは失敗します。  

### <a name="error-codes"></a>エラー コード

`--wait` パラメーターを使用した場合、操作の結果に応じて、`%ERRORLEVEL%` 環境変数は次のいずれかの値に設定されます。

  | **値** | **結果** |
  | --------- | ---------- |
  | 0 | 操作は正常に終了しました |
  | 3010 | 操作は正常に完了しましたが、インストールした製品を使用する前に再起動が必要です |
  | その他 | 失敗の状態が発生しました。詳細については、ログを参照してください |

## <a name="updating-a-network-install-layout"></a>ネットワーク インストール レイアウトを更新する

製品の更新プログラムが利用できるようになったら、[ネットワーク インストール レイアウトを更新し](update-a-network-installation-of-visual-studio.md)、更新されたパッケージを組み込むことが推奨されます。

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>以前の Visual Studio 2017 リリースのレイアウトを作成する方法

> [!NOTE]
> [VisualStudio.com](http://www.visualstudio.com) で入手可能な Visual Studio 2017 ブートストラップは、それを実行したときに利用できる最新の Visual Studio 2017 リリースをダウンロードし、インストールします。 Visual Studio ブートストラップを今日ダウンロードし、今日から 6 か月後に実行すると、6 か月後に利用できる Visual Studio 2017 リリースがインストールされます。 レイアウトを作成する場合、そのレイアウトから Visual Studio をインストールすると、レイアウトに存在する特定のバージョンの Visual Studio がインストールされます。 新しいバージョンがオンラインに存在するとしても、レイアウトに存在するバージョンの Visual Studio が取得されます。

旧バージョンの Visual Studio 2017 のレイアウトを作成する場合、https://my.visualstudio.com に進み、Visual Studio 2017 ブートストラップの "固定" バージョンをダウンロードできます。

### <a name="how-to-get-support-for-your-offline-installer"></a>オフライン インストーラーのサポートを受ける方法

オフライン インストールに問題が発生した場合は、マイクロソフトにお知らせください。 問題報告の最善の方法として、[[問題を報告する]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールを使用できます。 このツールでは、テレメトリとログを送信できます。これを、マイクロソフトは問題の診断と解決に役立てます。

他にも利用可能なサポート オプションがあります。 一覧については、[[ご意見]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ページをご覧ください。

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。
* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関する掲示板](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。  (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目
* [Visual Studio のインストール](install-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)
