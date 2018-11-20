---
title: Git リポジトリのセットアップ
description: Visual Studio for Mac で Git および Subversion を使用します。
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: c8d1cec438c0d942290997a6d51c4c0f2252bf8e
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296217"
---
# <a name="set-up-a-git-repository"></a>Git リポジトリのセットアップ

Git は、チームが同じドキュメントで同時に作業できるようにする分散型バージョン管理システムです。 つまり、すべてのファイルを含む 1 つのサーバーがありますが、この中央のソースからリポジトリがチェックアウトされるときには常に、リポジトリ全体がコンピューターにローカルで複製されます。

Git をバージョン コントロールに使用できるリモート ホストは多数ありますが、GitHub が最も一般的です。 次の例では GitHub ホストを使用しますが、Visual Studio for Mac ではバージョン管理のために任意の Git ホストを使用できます。

GitHub を使用する場合は、アカウントの作成と構成を完了してから、この記事の手順を実行してください。

## <a name="creating-a-remote-repo-on-github"></a>GitHub でのリモート リポジトリの作成

次の例では GitHub ホストを使用しますが、Visual Studio for Mac ではバージョン管理のために任意の Git ホストを使用できます。

Git リポジトリをセットアップするには、次の手順を実行します。

1. github.com で新しい Git リポジトリを作成します。

    ![新しい Git リポジトリを作成する](media/version-control-git1-sml.png)

2. リポジトリの名前、説明、およびプライバシーを設定します。 リポジトリは初期化**しない**でください。 次のように、.gitignore とライセンスを None に設定します。

    ![Git リポジトリの詳細を設定する](media/version-control-git2.png)

3. 次のページには、HTTPS または SSH アドレスの表示と、作成したリポジトリへのコピーに関するオプションが表示されます。

    ![アドレスの表示とコピー](media/version-control-git3.png)

   Visual Studio for Mac にこのリポジトリを指す HTTPS アドレスが必要です。

## <a name="publishing-an-existing-project"></a>既存のプロジェクトの発行

バージョン管理にまだ_含まれていない_既存のプロジェクトがある場合は、Git のセットアップで次の手順を使用します。

1.  Visual Studio for Mac でソリューション パッドからソリューション名を選択します。

2. メニュー バーで、**[バージョン コントロール]、[バージョン コントロールで発行]** の順に選択して、**[リポジトリの選択]** ダイアログを表示します。

    ![Visual Studio for Mac でチェックアウトを開始する](media/version-control-git4-sml.png)

    このメニュー項目がメニューで灰色表示されている場合は、ソリューション名が選択されていることを確認してください。

3. 次のように、**[登録済みリポジトリ]** タブを選択し、**[追加]** ボタンを押します。

    ![](media/version-control-git5.png)

4. ローカルで表示するリポジトリの名前を入力し、手順 3. の URL を貼り付けます。 リポジトリ構成ダイアログは次のようになります。 [OK] を押します。

    ![Git の詳細入力ダイアログ](media/version-control-git6.png)

    SSH を使用して Git に接続することもできます。

5. Git にアプリを発行してみる場合は、次のように、リポジトリを選択し、**[モジュール名]** と **[メッセージ]** の両方のテキスト フィールドに入力されていることを確認します。

    ![Git にプロジェクトを発行してみる](media/version-control-git7.png)

6. **[OK]** をクリックし、警告ダイアログの **[発行]** をクリックします。

7. Visual Studio for Mac 設定で Git 資格情報をまだ入力していない場合は、ここで入力します。 最初に、アクセス トークンを作成する必要があります。これはパスワードの代わりに使用されます。 アクセス トークンを作成していない場合は、Git の[アクセス トークン](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)に関するドキュメントの手順を実行してください。

8. ユーザー名と個人用アクセス トークンを入力して、**[OK]** を押します。

    ![Git のユーザー名とパスワードを入力する](media/version-control-git9-sml.png)

9. 数秒後に、初回コミットでソリューションが発行されます。 [バージョン コントロール] メニュー項目を参照して発行されたことを確認します。この時点で、次のように多くのオプションが示されます。

    ![バージョン管理メニュー](media/version-control-git10.png)

10. 追加の変更を開始してから、 **[変更をプッシュする]** を選択し、 **リモート** リポジトリに変更をプッシュします。 これで、適切なすべてのユーザーが github.com で表示できるようになります。

    ![リモート リポジトリに変更をプッシュする](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>新しいプロジェクトの発行

新しいプロジェクト ダイアログを使用して、Git で新しいプロジェクトを発行することができます。 これを有効にするには、**[バージョン コントロールに Git を使用する。]**  チェック ボックスをオンにします (以下のスクリーン ショットを参照)。 これでリポジトリが初期化され、オプションの .gitignore ファイルが追加されます。

![リモート リポジトリに変更をプッシュする](media/version-control-git12.png)

## <a name="check-out-an-existing-repository"></a>既存のリポジトリをチェックアウトする

ローカル コンピューター上にない、リモートにのみ存在する GitHub リポジトリを使用しなければならなくなる可能性があります。 Visual Studio for Mac ではこのリポジトリをすばやくチェックアウトできます。 お使いのコンピューターに複製するには、次の手順に従います。

1. メニュー バーで、**[バージョン コントロール] > [チェックアウト]** の順に選択します。

2. **[リポジトリへの接続]** タブが表示されます。

    ![詳細が入力された [リポジトリへの接続] タブ](media/version-control-git13.png)

3. リモート リポジトリの GitHub ページで、**[Clone or download]\(複製またはダウンロード\)** ボタンを押して、提供された URL をコピーします。

    ![URL が表示された github](media/version-control-git14.png)

4. **[リポジトリへの接続]** タブの **[URL]** エントリ フィールド内のすべてのテキストを置き換えます。手順 2 の画像に示すように、これによりこのタブの他のほとんどのフィールドに自動的に入力されます。

5. リポジトリの複製先のディレクトリを入力し、**[チェックアウト]** を押します。

> [!NOTE]
> リポジトリのサイズが 4 GB を超えている場合は、問題が発生する可能性があります。

## <a name="troubleshooting"></a>トラブルシューティング

空のリモート リポジトリでプロジェクトを初期化する際に問題が発生した場合は、次の手順を試すことができます。

1. ソリューション フォルダーに移動します。
1. **Command + Shift + .** キーを押して、 非表示のファイルとフォルダーを表示します。
1. **.git** フォルダーがある場合は、それを削除します。
1. **gitignore** ファイルがある場合は、それを削除します。
1. **Command + Shift + .** キーを押して、 ファイルとフォルダーを非表示にします。
1. VS for Mac でソリューションを開きます。
1. Solution Pad で、ソリューション ノードを選択します。
1. バージョン管理メニューを参照し、**[バージョン管理で発行]** を選択します。
1. 上記のチュートリアルの手順 6. 以降の手順に従います。

## <a name="see-also"></a>関連項目

- [Visual Studio でのバージョン コントロール (Windows)](/visualstudio/version-control/)