---
title: "Visual Studio 2017 の削除 | Microsoft Docs"
description: "Visual Studio を削除する方法について、ステップ バイ ステップで説明します。"
ms.custom: 
ms.date: 09/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: heaths
ms.author: heaths
manager: erickn
ms.openlocfilehash: 3c859b0023c9ea282afde837b17b7c93f3f4fbd7
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2017
---
# <a name="remove-visual-studio"></a>Visual Studio の削除

致命的なエラーが発生して Visual Studio の修復またはアンインストールができない場合は、`InstallCleanup.exe` ツールを実行してインストール ファイルと製品情報を削除することができます。 このツールの実行は修復またはアンインストールに失敗した場合の最終手段として行ってください。その他の Visual Studio のインストールやその他の製品の機能がアンインストールされ、後で修復が必要になる場合があります。

以下の手順では、以下の動作のコマンドライン スイッチでツールを実行することができます。

| スイッチ | 動作 |
| ------ | -------- |
| `-i`   | その他のスイッチが渡されていない場合、このスイッチが既定で、メインのインストール ディレクトリと製品情報のみが削除されます。 `InstallCleanup.exe` ツールを実行した後に同じバージョンを再インストールする予定がある場合は、この動作が適しています。 |
| `-f`   | このスイッチを指定すると、メインのインストール ディレクトリ、製品情報、そして他の Visual Studio のインストールまたは他の製品と共有できるインストール ディレクトリ外にインストールされているその他の多くの機能が削除されます。 この動作は、後で再インストールせずに Visual Studio を削除する場合に適しています。 |

1. Visual Studio インストーラーを閉じます。
2. 管理者のコマンド プロンプトを開きます。 管理者のコマンド プロンプトを開くには、以下の手順に従います。
   * **[スタート]** メニューで、 **[ファイル名を指定して実行]** (Start + R) をクリックします。
   * 「**cmd**」と入力します。
   * **[Command Prompt]** を右クリックし、**[管理者として実行]** をクリックします。
3. `InstallCleanup.exe` ユーティリティの完全なパスを入力して、必要なコマンドライン スイッチを渡します。 既定では、ユーティリティのパスは次のようになります。
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

通常は `%ProgramFiles(x86)%\Microsoft Visual Studio` にある `InstallCleanup.exe` が Visual Studio インストーラー ディレクトリの下に見つからない場合は、[Visual Studio のインストール](install-visual-studio.md)の手順に従い、ワークロード選択画面が表示されたら、ウィンドウを閉じて前の手順をもう一度実行します。

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。
* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関する掲示板](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。  (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目
* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [Visual Studio 2017 の更新](update-visual-studio.md)
* [Visual Studio 2017 の変更](modify-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
