---
title: "Visual Studio for Mac での Git リポジトリのセットアップ"
description: "Visual Studio for Mac で Git および Subversion を使用します。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 9f25eda17648ba7eb3c264660ee0eb3b8eee166c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---

# <a name="setting-up-a-git-repository"></a>Git リポジトリのセットアップ

Git は、チームが同じドキュメントで同時に作業できるようにする分散型バージョン管理システムです。 つまり、すべてのファイルを含む 1 つのサーバーがありますが、この中央のソースからリポジトリがチェックアウトされるときには常に、リポジトリ全体がコンピューターにローカルで複製されます。

バージョン管理のために Git を操作できるようにするリモート ホストは多数ありますが、GitHub が最も一般的です。 次の例では GitHub ホストを使用しますが、Visual Studio for Mac ではバージョン管理のために任意の Git ホストを使用できます。

GitHub を使用する場合は、次の手順に従う前に、アカウントを作成および構成していることを確認してください。 

## <a name="creating-a-remote-repo-on-github"></a>GitHub でのリモート リポジトリの作成

次の例では GitHub ホストを使用しますが、Visual Studio for Mac ではバージョン管理のために任意の Git ホストを使用できます。

Git リポジトリをセットアップするには、次の手順を実行します。

1. github.com で新しい Git リポジトリを作成します。

    ![新しい Git リポジトリを作成する](media/version-control-git1-sml.png)

2. リポジトリの名前、説明、およびプライバシーを設定します。 リポジトリは初期化**しない**でください。 次のように、.gitignore とライセンスを None に設定します。

    ![Git リポジトリの詳細を設定する](media/version-control-git2.png)

3. 次の場所では、HTTPS または SSH アドレスの表示と、作成したリポジトリへのコピーに関するオプションが示されます。

    ![アドレスの表示とコピー](media/version-control-git3.png) Visual Studio for Mac にこのリポジトリを指す HTTP アドレスが必要です。


## <a name="publishing-an-existing-project"></a>既存のプロジェクトの発行

4. Visual Studio for Mac で開いたプロジェクトに戻ります。 

5. メニュー バーで、次のように **[バージョン管理]、[Publish in Version Control…]\(バージョン管理で発行...\)** の順に選択します。

    ![Visual Studio for Mac でチェックアウトを開始する](media/version-control-git4-sml.png)

6. これで、**[リポジトリの選択]** ダイアログが表示されます。 次のように、**[登録済みリポジトリ]** タブを選択し、**[追加]** ボタンを押します。

    ![](media/version-control-git5.png)

7. ローカルで表示するリポジトリの名前を入力し、手順 3. の URL を貼り付けます。 リポジトリ構成ダイアログは次のようになります。 [OK] を押します。 

    ![Git の詳細入力ダイアログ](media/version-control-git6.png)

    Git に接続する際に SSH を使用することもできます。

8. Git にアプリを発行してみる場合は、次のように、作成したリポジトリを選択し、**[モジュール名]** と **[メッセージ]** の両方のテキスト フィールドに入力されていることを確認します。

    ![Git にプロジェクトを発行してみる](media/version-control-git7.png)

9. **[OK]** をクリックし、警告ダイアログの **[発行]** をクリックします。

10. Visual Studio for Mac 設定で Git 資格情報をまだ入力していない場合は、ここで入力します。 最初に、アクセス トークンを作成する必要があります。これはパスワードの代わりに使用されます。 これを行うには、Git の[アクセス トークン](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)に関するドキュメントに示されている手順に従います。

11. ユーザー名と個人用アクセス トークンを入力して、**[OK]** を押します。

    ![Git のユーザー名とパスワードを入力する](media/version-control-git9-sml.png)

12. 数秒後に、初回コミットでソリューションが発行されます。 バージョン管理メニュー項目を参照してこれを確認します。この時点で、次のように多くのオプションが示されます。 

    ![バージョン管理メニュー](media/version-control-git10.png)

13. 追加の変更を開始してから、**[変更をプッシュする...]** を選択し、**リモート** リポジトリに変更をプッシュします。 これで、適切なすべてのユーザーが github.com で表示できるようになります。 

    ![リモート リポジトリに変更をプッシュする](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>新しいプロジェクトの発行

新しいプロジェクト ダイアログを使用して、Git で新しいプロジェクトを発行することができます。 これを有効にするには、**[バージョン コントロールに Git を使用する。]**  チェック ボックスをオンにします (以下のスクリーン ショットを参照)。 これでリポジトリが初期化され、オプションの .gitignore ファイルが追加されます。

![リモート リポジトリに変更をプッシュする](media/version-control-git12.png)

## <a name="troubleshooting"></a>トラブルシューティング

空のリモート リポジトリでプロジェクトを初期化する際に問題が発生した場合は、次の手順を試すことができます。

- ソリューション フォルダーに移動します。
- `Command + Shift + . ` キーを押して、非表示のファイルとフォルダーを表示します。
- `.git` フォルダーがある場合は、それを削除します。
- `gitignore` ファイルがある場合は、それを削除します。
- `Command + Shift + . ` キーを押して、ファイルとフォルダーを非表示にします。
- VS for Mac でソリューションを開きます。
- Solution Pad で、ソリューション ノードを選択します。
- バージョン管理メニューを参照し、**[バージョン管理で発行]** を選択します。
- 上記のチュートリアルの手順 6. 以降の手順に従います。
