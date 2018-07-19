---
title: Visual Studio 2017 を更新する
description: Visual Studio を最新のリリースに更新する詳細な手順を説明します。
ms.date: 04/23/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- update Visual Studio
- change visual studio
- changing Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a4d02cca5a48dc17bf125cf83267945ecc8f514
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36281197"
---
# <a name="update-visual-studio-2017-to-the-most-recent-release"></a>Visual Studio 2017 を最新リリースに更新する

常に最新の機能、修正、改善を利用できるように、Visual Studio 2017 の[最新バージョン](/visualstudio/releasenotes/vs2017-relnotes)に更新することをお勧めします。

リリース前に試したい場合は、次バージョンの[プレビュー リリース](/visualstudio/releasenotes/vs2017-preview-relnotes)をダウンロードすることもできます。

> [!IMPORTANT]
> Visual Studio をインストール、更新、または変更するには、管理アクセス許可を持つアカウントでログオンする必要があります。 詳細については、「[ユーザー アクセス許可と Visual Studio](../ide/user-permissions-and-visual-studio.md)」を参照してください。

## <a name="update-visual-studio-2017-version-156-or-later"></a>Visual Studio 2017 バージョン 15.6 以降を更新する

IDE 内から直接使用しやすくするために、インストールと更新プログラムのエクスペリエンスが整理されました。 ここでは、バージョン 15.6 以降から新しいバージョンの Visual Studio に更新する方法について説明します。

### <a name="use-the-notifications-hub"></a>通知ハブを使用する

更新プログラムがある場合、Visual Studio には対応する通知フラグが表示されます。

1. 作業内容を保存します。

2. 通知フラグを選択して**通知**ハブを開き、インストールする更新プログラムを選択します。

  ![通知ハブを使用して Visual Studio 2017 を更新する](media/vs-install-notifications-hub-15dot6.png "Visual Studio 2017 の 通知ハブ")

3. **[更新]** ダイアログ ボックスが開いたら、**[今すぐ更新]** を選択します。

    ![通知ハブから [更新] ダイアログ ボックスを使用して Visual Studio 2017 を更新する](media/vs-update-now-from-notifications-hub.png "Visual Studio の通知ハブの [更新] ダイアログ ボックス")

     [ユーザー アクセス制御] ダイアログ ボックスが開いたら、**[はい]** を選択します。 [お待ちください] ダイアログが表示されることがあります。処理が完了すると、Visual Studio インストーラーが開き、更新が開始されます。

     ![バージョン 15.6 の Visual Studio インストーラーの新しいエクスペリエンス](media/visual-studio-15dot6-installer.png "バージョン 15.6 の Visual Studio インストーラーの新しいエクスペリエンス")

     更新が続行されます。 処理が完了すると、Visual Studio が再起動されます。

     > [!NOTE]
     > Visual Studio を管理者モードで実行する場合は、更新後に Visual Studio を手動で再起動する必要があります。

### <a name="use-the-ide"></a>IDE を使用する

更新プログラムを確認し、Visual Studio のメニュー バーから更新プログラムをインストールすることができます。

1. 作業内容を保存します。

2. **[ヘルプ]** > **[更新プログラムの確認]** を選択します。

     ![Visual Studio バージョン 15.6 の新しい [ヘルプ] メニュー](media/vs-help-menu-check-for-updates.png "Visual Studio バージョン 15.6 の新しい [ヘルプ] メニュー")

3. **[更新]** ダイアログ ボックスが開いたら、**[今すぐ更新]** を選択します。

   前のセクションと同様に更新が実行され、更新が正常に完了すると Visual Studio が再起動されます。

   > [!NOTE]
   > Visual Studio を管理者モードで実行する場合は、更新後に Visual Studio を手動で再起動する必要があります。

### <a name="use-the-visual-studio-installer"></a>Visual Studio インストーラーを使用する

Visual Studio 2017 の以前のバージョンと同様に、Visual Studio インストーラーを使用して更新プログラムをインストールすることもできます。

1. 作業内容を保存します。

2. インストーラーを開きます。 必要に応じて、Visual Studio インストーラーを更新してから続行します。

  > [!NOTE]
  > Windows 10 を実行しているコンピューターの場合、**V** という文字の下に **Visual Studio インストーラー**と表示されるか、**M** という文字の下に **Microsoft Visual Studio インストーラー**と表示されます。

2. インストーラーの **[製品]** ページで、インストールされている Visual Studio のエディションを探します。

3. 更新プログラムが使用可能な場合は、**[更新]** ボタンが表示されます  (使用可能な更新プログラムがあるかどうかをインストーラーが判断するために数秒かかる場合があります)。

  **[更新]** ボタンを選択して更新プログラムをインストールします。

     ![Visual Studio インストーラーを使用して Visual Studio 2017 を更新する](media/update-visual-studio.png "Visual Studio インストーラーを使用して Visual Studio 2017 を更新する")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Visual Studio 2017 バージョン 15.5 以前のバージョンを更新する

以前のバージョンを使用している場合、Visual Studio 2017 バージョン 15.0 からバージョン 15.5 の更新プログラムを適用するには、次の手順を実行します。

### <a name="update-by-using-the-notifications-hub"></a>通知ハブを使用して更新する

1. 更新プログラムがある場合、Visual Studio には対応する通知フラグが表示されます。

  ![通知ハブを使用して Visual Studio 2017 を更新する](media/notification-flag.png "Visual Studio の更新プログラムがあることを知らせる通知フラグ")

  通知フラグを選択して、**通知**ハブを開きます。

  ![通知ハブを使用して Visual Studio 2017 を更新する](media/notifications-hub.png "Visual Studio の通知ハブ")

2. **["Visual Studio 更新プログラム" が使用可能です]** を選択すると、**[拡張機能と更新プログラム]** ダイアログ ボックスが開きます。

  ![通知ハブを使用して Visual Studio 2017 を更新する](media/notifications-hub-select.png "Visual Studio の通知ハブ")

3. **[拡張機能と更新プログラム]** ダイアログ ボックスで、**[更新]** ボタンを選択します。

  ![通知ハブを使用して Visual Studio 2017 を更新する](media/notifications-extensions-and-updates.png "Visual Studio の [拡張機能と更新プログラム] ダイアログ")

#### <a name="more-about-visual-studio-notifications"></a>Visual Studio の通知の詳細

Visual Studio は、Visual Studio 自体またはいずれかのコンポーネントの更新プログラムが入手可能な場合に通知します。また、Visual Studio 環境で特定のイベントが発生した場合も通知します。

* 通知フラグが黄色の場合は、インストールできる Visual Studio 製品の更新プログラムが存在します。
* 通知フラグが赤の場合は、ライセンスに問題があります。
* 通知フラグが黒の場合は、確認のためのオプション メッセージまたは情報メッセージが存在します。

通知フラグを選択して**通知**ハブを開いてから、操作する通知を選択します。 または、通知を無視するか破棄するかを選択します。

 ![通知ハブでオプション メッセージまたは情報メッセージを表示する](media/notification-flag-optional.png "Visual Studio のオプション メッセージまたは情報メッセージの通知フラグ")

通知を無視することを選択した場合は、Visual Studio で表示されなくなります。 無視される通知のリストをリセットする場合は、通知ハブの **[設定]** ボタンを選択します。

   ![通知オプションを表示するために通知ハブの [設定] ボタンを選択する](media/vs-notifications-hub-settings-button.png "通知オプションを表示するために通知ハブの [設定] ボタンを選択する")

### <a name="update-by-using-the-visual-studio-installer"></a>Visual Studio インストーラーを使用して更新する

1. インストーラーを開きます。 続行する前に、インストーラーの更新が必要な場合があります。 更新が必要な場合は、更新するよう求められます。

  > [!NOTE]
  > Windows 10 を実行しているコンピューターの場合、**V** という文字の下に **Visual Studio インストーラー**と表示されるか、**M** という文字の下に **Microsoft Visual Studio インストーラー**と表示されます。

2. インストーラーの **[製品]** ページで、インストールされている Visual Studio のエディションを探します。

3. 更新プログラムが使用可能な場合は、**[更新]** ボタンが表示されます  (使用可能な更新プログラムがあるかどうかをインストーラーが判断するために数秒かかる場合があります)。

  **[更新]** ボタンを選択して更新プログラムをインストールします。

     ![Visual Studio インストーラーを使用して Visual Studio 2017 を更新する](media/update-visual-studio.png "Visual Studio インストーラーを使用して Visual Studio 2017 を更新する")

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://visualstudio.microsoft.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [Visual Studio 2017 の変更](modify-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
