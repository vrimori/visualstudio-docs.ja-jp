---
title: "インストールの問題のトラブルシューティング | Microsoft Docs"
description: "{{プレースホルダー}}"
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: timsneath
ms.author: tims
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: d8125873ab5a92d9af26c556cb2f953a606c28d9
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-failures"></a>Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング

## <a name="symptoms"></a>現象
Microsoft Visual Studio 2017 をインストールまたは更新しようとすると、操作が失敗する。

## <a name="workaround"></a>回避策
この問題を回避するには、次の手順を実行します。

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>手順 1 - この問題が既知の問題であるかどうかを確認する
Visual Studio インストーラーには、Microsoft が修正に取り組んでいる問題がいくつかあります。 問題の回避策があるかどうか、[リリース ノートの既知の問題に関するセクション](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#KIinstall)で確認してください。

### <a name="step-2---check-with-the-developer-community"></a>手順 2 - 開発者コミュニティを確認する
[Visual Studio の開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/8/index.html) でエラー メッセージを検索してください。 コミュニティの他のメンバーが、問題の解決策を文書化している可能性があります。

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>手順 3 - Visual Studio インストーラーのディレクトリを削除してアップグレードの問題を修正する
Visual Studio インストーラーのブートストラップは、Visual Studio インストーラーの残りをインストールする最小限の軽量な実行可能ファイルです。 Visual Studio インストーラー ファイルを削除して、ブートストラップを再実行すると、いくつかの更新エラーを解決できる場合があります。 この操作を行うには、次の手順に従います。

1. Visual Studio インストーラーを閉じます。
2. Visual Studio インストーラーのディレクトリを削除します。 通常、ディレクトリは、C:\Program Files (x86)\Microsoft Visual Studio\Installer にあります。
3. Visual Studio インストーラーのブートストラップを実行します。 [ダウンロード] フォルダーのブートストラップのファイル名には ```vs_[Visual Studio edition]__*.exe``` のパターンが使用されている場合があります。 アプリケーションが見つからない場合は、「[Visual Studio のダウンロード](https://www.visualstudio.com/downloads/)」ページに移動し、Visual Studio のお使いのエディションの **[ダウンロード]** をクリックすると、ブートストラップをダウンロードできます。 この実行可能ファイルを実行して、インストールのメタデータをリセットします。
4. Visual Studio のインストールまたは更新を再度試します。 インストーラーのエラーが続く場合は、この次の手順 4 に進んでください。
<br/>**注:** この手順では Visual Studio インストーラー ファイルが再インストールされ、インストールのメタデータがリセットされます。 

### <a name="step-4---report-a-problem"></a>手順 4 - 問題を報告する
ファイルの破損など、一部の状況では、問題をケースごとに調べなければならない場合があります。

1. [Microsoft Visual Studio および .NET Framework のログ収集ツール](https://www.microsoft.com/en-us/download/details.aspx?id=12493)をダウンロードして、実行します。 このツールは、Visual Studio、.NET Framework、SQL Server のインストールで入手できるセットアップ ログを収集し、コンパイルします。
2. Visual Studio インストーラーを開き、**[問題の報告]** をクリックして、Visual Studio フィードバック ツールを開きます。
![[フィードバックの送信] ボタンからフィードバック ツールを開くことができます](media/report-a-problem.png)
3. 問題のレポートにタイトルを付け、関連する詳細を入力します。 **[次へ]** をクリックして **[添付ファイル]** セクションに移動し、生成されたログ ファイルを添付します (通常、ファイルは %TEMP%\vslogs.zip にあります)。
![[新しい問題を報告する] ボタンを選択し、手順に従います](media/problem-report-details.png)
4. **[次へ]** をクリックして問題レポートを確認し、**[送信]** をクリックします。

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>手順 5 - InstallCleanup.exe を実行してインストール ファイルをクリーンアップする
最後の手段として、InstallCleanup.exe を実行することができます。 InstallCleanup.exe は、Visual Studio インストーラーのパッケージに含まれるユーティリティで、インストール ファイルをクリーンアップします。 これによって全体が再インストールされるわけではありません。 このユーティリティは、Visual Studio 2017 のキャッシュとインスタンス データを削除します。

1. Visual Studio インストーラーを閉じます。
2. 管理者のコマンド プロンプトを開きます。 この操作を行うには、次の手順に従います。
   * **[スタート]** メニューで、 **[ファイル名を指定して実行]** (Start + R) をクリックします。
   * 「**cmd**」と入力します。
   * **[コマンド プロンプト]** を右クリックしてから、**[管理者として実行]** を選択します。
3. InstallCleanup.exe ユーティリティの完全なパスを入力し、コマンド ライン スイッチ -f を渡します。 既定では、ユーティリティのパスは次のようになります。
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. 手順 3 で説明したブートス トラップを再実行します。
5. Visual Studio のインストールまたは更新を再度試します。

## <a name="how-to-troubleshoot-an-offline-installer"></a>オフライン インストーラーをトラブルシューティングする方法
次にローカル レイアウトからのインストール時の既知の問題と、便利な回避策をいくつか紹介します。

| 懸案事項       | アイテム                   | ソリューション |
| ----------- | ---------------------- | -------- |
| ユーザーにファイルへのアクセス権がない。 | アクセス許可 (ACL) | オフライン インストールを共有する*前*に、他のユーザーに読み取りアクセス権を付与するように、必ずアクセス許可 (ACL) を調整してください。 |
| 新しいワークロード、コンポーネント、または言語をインストールできない。  | `--layout`  | 部分レイアウトからインストールし、以前のレイアウトで使用できないワークロード、コンポーネント、または言語を選択した場合、インターネットにアクセスできることを確認してください。 |



