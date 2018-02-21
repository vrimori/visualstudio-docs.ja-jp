---
title: "Visual Studio 2017 の更新 | Microsoft Docs"
description: "Visual Studio を更新する方法について、ステップ バイ ステップで説明します。"
ms.date: 12/18/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- update Visual Studio
- change visual studio
- changing Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8e61def66e68d7f889349d0e7b7337238e220dce
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="update-visual-studio-2017-to-the-most-recent-release"></a>Visual Studio 2017 を最新リリースに更新する
Microsoft は、機能の拡張とお客様から報告された問題の修正のために、Visual Studio を頻繁に更新します。 [最適化された最新リリースの Visual Studio](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#release-history) を常に使用できるように、Visual Studio を更新してください。 ここではその方法を説明します。

>[!IMPORTANT]
>Visual Studio をインストール、更新、または変更するには、管理アクセス許可を持つアカウントでログオンする必要があります。 詳細については、「[ユーザー アクセス許可と Visual Studio](../ide/user-permissions-and-visual-studio.md)」を参照してください。

## <a name="update-by-using-the-notifications-hub"></a>通知ハブを使用して更新する
1. 更新プログラムが存在する場合、Visual Studio に通知フラグが表示されます。

  ![通知ハブを使用して Visual Studio 2017 を更新する](media/notification-flag.png "Visual Studio の更新プログラムがあることを知らせる通知フラグ")

  通知フラグを選択して、**通知**ハブを開きます。

  ![通知ハブを使用して Visual Studio 2017 を更新する](media/notifications-hub.png "Visual Studio の通知ハブ")

2. **["Visual Studio 更新プログラム" が使用可能です]** を選択すると、**[拡張機能と更新プログラム]** ダイアログ ボックスが開きます。

  ![通知ハブを使用して Visual Studio 2017 を更新する](media/notifications-hub-select.png "Visual Studio の通知ハブ")

3. **[拡張機能と更新プログラム]** ダイアログ ボックスで、**[更新]** ボタンを選択します。

  ![通知ハブを使用して Visual Studio 2017 を更新する](media/notifications-extensions-and-updates.png "Visual Studio の [拡張機能と更新プログラム] ダイアログ")

### <a name="more-about-visual-studio-notifications"></a>Visual Studio の通知の詳細

Visual Studio は、Visual Studio 自体またはいずれかのコンポーネントの更新プログラムが入手可能な場合に通知します。また、Visual Studio 環境で特定のイベントが発生した場合も通知します。

* 通知フラグが黄色の場合は、インストールできる Visual Studio 製品の更新プログラムが存在します。
* 通知フラグが赤の場合は、ライセンスに問題があります。
* 通知フラグが黒の場合は、確認のためのオプション メッセージまたは情報メッセージが存在します。

通知フラグを選択して**通知**ハブを開いてから、操作する通知を選択します。 または、通知を無視するか破棄するかを選択します。

 ![通知ハブでオプション メッセージまたは情報メッセージを表示する](media/notification-flag-optional.png "Visual Studio のオプション メッセージまたは情報メッセージの通知フラグ")

通知を無視することを選択した場合は、Visual Studio で表示されなくなります。 無視される通知のリストをリセットする場合は、通知ハブの **[設定]** ボタンをクリックします。

   ![通知オプションを表示するために通知ハブの [設定] ボタンを選択する](media/vs-notifications-hub-settings-button.png "通知オプションを表示するために通知ハブの [設定] ボタンを選択する")

## <a name="update-by-using-the-visual-studio-installer"></a>Visual Studio インストーラーを使用して更新する
1.  インストーラーを開きます。 続行する前に、インストーラーの更新が必要な場合があります。 更新が必要な場合は、更新するよう求められます。
 >[!NOTE]
 > Windows 10 を実行しているコンピューターの場合、**V** という文字の下に **Visual Studio インストーラー**と表示されるか、**M** という文字の下に **Microsoft Visual Studio インストーラー**と表示されます。

2.  インストーラーの **[製品]** ページで、インストールされている Visual Studio のエディションを探します。

3.  更新プログラムが使用可能な場合は、**[更新]** ボタンが表示されます  (使用可能な更新プログラムがあるかどうかをインストーラーが判断するために数秒かかる場合があります)。

  **[更新]** ボタンを選択して更新プログラムをインストールします。

     ![Visual Studio インストーラーを使用して Visual Studio 2017 を更新する](media/update-visual-studio.png "Visual Studio インストーラーを使用して Visual Studio 2017 を更新する")

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。
* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関する掲示板](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。  (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目
* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [Visual Studio 2017 の変更](modify-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
