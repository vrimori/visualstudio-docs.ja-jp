---
title: Visual Studio サブスクリプションにライセンスを割り当てる | Microsoft Docs
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 07/16/2018
ms.topic: conceptual
description: 管理者がサブスクライバーにライセンスを割り当てる方法を説明します
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 6f0bbded7682bd8f7162ae415c6c83711df04a04
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931234"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Visual Studio サブスクリプション管理者ポータルでライセンスを割り当てる

Visual Studio サブスクリプションの管理者は、管理者ポータルを使用して、個々のユーザーおよびユーザーのグループにサブスクリプションを割り当てることができます。

ユーザーのグループの場合、一度に 1 つずつグループにサブスクリプションを割り当てることも、**[一括追加]** 機能を使用して迅速かつ簡単にサブスクリプション情報でサブスクライバーの一覧をアップロードすることも可能です。

## <a name="individual-assignments"></a>個別の割り当て

新しいユーザーがサブスクリプションの特典にアクセスできるように、新しいユーザーに Visual Studio サブスクリプション ライセンスを割り当てる方法を次に示します。

1. [管理者ポータル](https://manage.visualstudio.com)にサインインします。

2. 1 人の Visual Studio サブスクライバーにライセンスを割り当てるには、テーブルの上部にある **[追加]** を選択します。
   > [!div class="mx-imgBorder"]
   > ![1 人のサブスクライバーを追加する](media/add-single-subscriber.png)

3. フォームのフィールドに新しいサブスクライバーの情報を入力します。 組織が Azure Active Directory を使っている場合は、このフィールドを使って現在のディレクトリのユーザーを検索し、検索結果から適切なユーザーを選ぶことができます。 ユーザーを選ぶと、名前、サインイン メール アドレス、通知メール アドレスが自動的に設定されます。
   > [!div class="mx-imgBorder"]
   > ![新しい通知メール アドレスを追加する](media/add-new-subscriber-notification-email.png)

    このサブスクライバーが [Visual Studio サブスクリプション ポータル](https://my.visualstudio.com?wt.mc_id=o~msft~docs)にサインインするときにソフトウェアのダウンロードにアクセスできるようにする場合は、**[ダウンロードの設定]** セクションでダウンロードのトグルをオンのままにします。 ダウンロードを無効にすると、ユーザーはソフトウェアのダウンロードにアクセスできなくなりますが、サブスクリプションに含まれる他のすべての特典には引き続きアクセスできます。
   > [!div class="mx-imgBorder"]
   > ![ダウンロードにアクセスする](media/access-to-downloads.png)

    サブスクライバーが受け取る情報の言語を変更する場合は、**[Communication Preferences]\(通信設定\)** セクションで変更できます。
   > [!div class="mx-imgBorder"]
   > ![通知メールを送信するときに使用する言語を変更する](media/change-subscriber-communication-preference.png)

    サブスクリプションに独自の参照メモを追加する場合は、**[Add reference]\(参照の追加\)** セクションで追加できます。
   > [!div class="mx-imgBorder"]
   > ![サブスクリプションごとに独自の参照メモを追加する](media/add-subscriber-reference-notes.png) 

    オプションの選択とサブスクライバーのデータの入力が終わったら、**[Add Subscriber]\(サブスクライバーの追加\)** フライアウトの下部にある **[追加]** を選択します。
   > [!div class="mx-imgBorder"]
   > ![[追加] ボタンを選択する](media/add-button.png)

4. サブスクライバーを追加すると、詳細な説明が記載された割り当てメールがサブスクライバーに自動的に送信されます。 サブスクライバーを選択して、上部メニューの **[再送信]** ボタンをクリックすることで、いつでも割り当てメールを送信し直すことができます。
   > [!div class="mx-imgBorder"]
   > ![必要なときにいつでもアクティブ化メールを任意または複数のユーザーに再送する](media/resend-subscriber-activation-emails.png) 

## <a name="bulk-assignments"></a>一括割り当て

1. 複数のサブスクライバーを一度に追加するには、**[サブスクライバーの管理]** タブに移動します。上部リボンの **[一括追加]** をクリックします。
   > [!div class="mx-imgBorder"]
   > ![複数のサブスクライバーを追加する](media/add-multiple-subscribers.png)

2. 一括割り当てでは、Microsoft Excel テンプレートを使ってサブスクライバーをアップロードします。 [Upload Multiple Subscribers]\(複数のサブスクライバーのアップロード\) ダイアログ ボックスで、**[ダウンロード]** をクリックしてテンプレートをダウンロードします。
   > [!div class="mx-imgBorder"]
   > ![複数のサブスクライバーをアップロードするための Excel テンプレートをダウンロードする](media/download-template-upload-subscribers.png)
   > 
   > [!NOTE]
   > 常にこのテンプレートの最新バージョンをダウンロードしてください。 古いバージョンを使うと、一括アップロードが失敗する可能性があります。

3. Excel スプレッドシートのフィールドに、サブスクリプションを割り当てるユーザーの情報を入力します。 *[Reference]* は省略可能なフィールドです。完成したらローカルにファイルを保存します。

   問題なくアップロードできるよう、次のベスト プラクティスに従ってください。

    - フォームのどのフィールドにもコンマが含まれていないことを確認します。
    - フォームのフィールドの前後のスペースを削除します。
    - ユーザーの名前の名または姓が 2 つの部分からなる場合、それらの間に余分なスペースがないようにします (たとえば、"Maggie May" のように 2 つの部分からなる名前は、"MaggieMay" と入力する必要があります。システムは余分なスペースを除去しません)。

4. Visual Studio サブスクリプション管理ポータルに戻ります。 **[Upload Multiple Subscribers]\(複数のサブスクライバーのアップロード\)** ダイアログ ボックスで、**[参照]** をクリックします。
   > [!div class="mx-imgBorder"]
   > ![複数のサブスクライバーをアップロードするために保存したテンプレートを参照する](media/bulk-add-browse-saved-template.png)

5. 保存した Excel ファイルを選んで、**[OK]** をクリックします。
   > [!div class="mx-imgBorder"]
   > ![複数のサブスクライバーをアップロードするための Excel テンプレートをアップロードする](media/bulk-upload-subscribers.png)

    アップロードの進行状況を示すダイアログが表示されます。

    テンプレートにエラーが含まれていると、アップロードは失敗してエラーが表示されるので、テンプレートを修正して一括アップロードを再試行します。
   > [!div class="mx-imgBorder"]
   > ![複数サブスクライバーのアップロードが失敗した場合のエラー メッセージ](media/bulk-add-template-failed.png)

    アップロードが成功すると、サブスクライバーの一覧と確認メッセージが表示されます。
   > [!div class="mx-imgBorder"]
   > ![複数サブスクライバーのアップロードが成功した場合の確認メッセージ](media/bulk-add-template-success.png)
