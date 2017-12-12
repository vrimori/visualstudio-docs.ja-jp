---
title: "インストールの問題のトラブルシューティング | Microsoft Docs"
description: "ときには、問題が発生してしまうことがあります。 Visual Studio のインストールまたはアップグレードが失敗した場合、このページが役に立ちます。"
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: timsneath
ms.author: tims
manager: ghogen
ms.openlocfilehash: f0f71dab64a99965facac9ccaa0fff9b53a6e3f6
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング

## <a name="symptoms"></a>現象
Visual Studio 2017 をインストールまたは更新しようとすると、操作が失敗する。

## <a name="workaround"></a>回避策
この問題を回避するには、次の手順を実行します。

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>手順 1 - この問題が既知の問題であるかどうかを確認する
Visual Studio インストーラーには、Microsoft が修正に取り組んでいる問題がいくつかあります。 問題の回避策があるかどうか、[リリース ノートの既知の問題に関するセクション](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#known-issues)で確認してください。

### <a name="step-2---check-with-the-developer-community"></a>手順 2 - 開発者コミュニティを確認する
[Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/8/index.html)でエラー メッセージを検索します。 コミュニティの他のメンバーが、問題の解決策を文書化している可能性があります。

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>手順 3 - Visual Studio インストーラーのディレクトリを削除してアップグレードの問題を修正する
Visual Studio インストーラーのブートストラップは、Visual Studio インストーラーの残りをインストールする最小限の軽量な実行可能ファイルです。 Visual Studio インストーラー ファイルを削除して、ブートストラップを再実行すると、いくつかの更新エラーを解決できる場合があります。

**注:** 次のアクションを実行すると、Visual Studio インストーラー ファイルが再インストールされ、インストール メタデータがリセットされます。

1. Visual Studio インストーラーを閉じます。
2. Visual Studio インストーラーのディレクトリを削除します。 通常、ディレクトリは `C:\Program Files (x86)\Microsoft Visual Studio\Installer` です。
3. Visual Studio インストーラーのブートストラップを実行します。 [ダウンロード] フォルダーのブートストラップのファイル名には `vs_[Visual Studio edition]__*.exe` のパターンが使用されている場合があります。 アプリケーションが見つからない場合は、「[Visual Studio のダウンロード](https://www.visualstudio.com/downloads/)」ページに移動し、Visual Studio のお使いのエディションの **[ダウンロード]** をクリックして、ブートストラップをダウンロードできます。 実行可能ファイルを実行して、インストール メタデータをリセットします。
4. Visual Studio のインストールまたは更新を再度試します。 インストーラーのエラーが続く場合は、次の手順に進みます。

### <a name="step-4---report-a-problem"></a>手順 4 - 問題を報告する
ファイルの破損など、一部の状況では、問題をケースごとに調べなければならない場合があります。

1. セットアップ ログを収集します。 詳細については、「[Visual Studio のインストール ログを取得する方法](#how-to-get-the-visual-studio-installation-logs)」をご覧ください。
2. Visual Studio インストーラーを開き、**[問題の報告]** をクリックして、Visual Studio フィードバック ツールを開きます。
![[フィードバックの送信] ボタンからフィードバック ツールを開くことができます](media/report-a-problem.png)
3. 問題のレポートにタイトルを付け、関連する詳細を入力します。 **[次へ]** をクリックして **[添付ファイル]** セクションに移動し、生成されたログ ファイルを添付します (通常、ファイルは `%TEMP%\vslogs.zip` にあります)。
4. **[次へ]** をクリックして問題レポートを確認し、**[送信]** をクリックします。

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>手順 5 - InstallCleanup.exe を実行してインストール ファイルを削除する
最後の手段として、[Visual Studio を削除](remove-visual-studio.md)し、すべてのインストール ファイルと製品情報を削除できます。

1. 「[Visual Studio の削除](remove-visual-studio.md)」の説明に従ってください。
2. 「[手順 3 - Visual Studio インストーラーのディレクトリを削除してアップグレードの問題を修正する](#step-3--delete-the-visual-studio-installer-directory-to-fix-upgrade-problems)」で説明したブートストラップを再実行します。
3. Visual Studio のインストールまたは更新を再度試します。

### <a name="step-6---contact-us-optional"></a>手順 6 - 問い合わせる (省略可能)
他のどの手順でも正常にインストールできない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

## <a name="how-to-troubleshoot-an-offline-installer"></a>オフライン インストーラーをトラブルシューティングする方法
次にローカル レイアウトからのインストール時の既知の問題と、便利な回避策をいくつか紹介します。

| 懸案事項       | アイテム                   | ソリューション |
| ----------- | ---------------------- | -------- |
| ユーザーにファイルへのアクセス権がない。 | アクセス許可 (ACL) | オフライン インストールを共有する*前*に、他のユーザーに読み取りアクセス権を付与するように、必ずアクセス許可 (ACL) を調整してください。 |
| 新しいワークロード、コンポーネント、または言語をインストールできない。  | `--layout`  | 部分レイアウトからインストールし、その部分レイアウトには以前ダウンロードしなかったワークロード、コンポーネント、または言語を選択した場合は、インターネットにアクセスできることを確認してください。 |

## <a name="how-to-get-the-visual-studio-installation-logs"></a>Visual Studio のインストール ログを取得する方法
セットアップ ログは、インストールに関する問題の多くをトラブルシューティングするために必要です。 Visual Studio インストーラーの [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) を使用して問題を送信するとき、レポートには自動でこれらのログが含まれます。

Microsoft サポートに連絡する場合、[Microsoft Visual Studio と .NET Framework ログ収集ツール](https://aka.ms/vscollect)を使用して収集したセットアップ ログの提供が必要になる場合があります。 このログ収集ツールは、Visual Studio 2017 にインストールされている .NET Framework、Windows SDK、SQL Server などのすべてのコンポーネントからセットアップ ログを収集します。 また、コンピューター情報、Windows インストーラーのインベントリ、Visual Studio インストーラーの Windows イベント ログ情報、Windows インストーラー、システムの復元に関する情報を収集します。

ログを収集するには:

1. [ツールをダウンロード](https://aka.ms/vscollect)します。
2. 管理コマンド プロンプトを開きます。
3. ツールを保存したディレクトリから `Collect.exe` を実行します。
4. `%TEMP%` ディレクトリで結果の `vslogs.zip` ファイルを探します (例: `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`)。

> [!NOTE]
> このツールは、インストールの実行に失敗したときと同じユーザー アカウントで実行する必要があります。 別のユーザー アカウントでこのツールを実行する場合は、`–user:<name>` オプションを設定して、インストールの実行に失敗したユーザー アカウントを指定します。 追加オプションや使用に関する情報を収集するには、管理コマンド プロンプトで `Collect.exe -?` を実行します。

## <a name="more-support-options"></a>その他のサポート オプション

Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。

他のいくつかのオプションを次に示します。

* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関する掲示板](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます  (これには [GitHub](https://github.com/) アカウントが必要です)。

## <a name="see-also"></a>関連項目
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [Visual Studio インスタンスの検出および管理用のツール](tools-for-managing-visual-studio-instances.md)
* [Visual Studio 2017 の削除](remove-visual-studio.md)
