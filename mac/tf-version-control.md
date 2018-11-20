---
title: Team Foundation バージョン管理 (TFVC)
description: Team Foundation バージョン管理 (TFVC) で Team Foundation Server または Azure DevOps Services に接続します。
author: conceptdev
ms.author: crdun
ms.date: 09/05/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 9cb6a466d764c85012477fb2d849c05920908f02
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295931"
---
# <a name="connecting-to-team-foundation-version-control"></a>Team Foundation バージョン管理に接続する

> [!NOTE]
> 現在、Team Foundation バージョン管理サポートはプレビューとして提供されており、一部の機能は完全に動作していません。 [開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/41/index.html)で問題についてフィードバックしてください。 今後、さらに変更される予定です。

Azure Repos には、バージョン管理のモデルが 2 つあります。分散型バージョン管理の Git と、集中型バージョン管理の Team Foundation バージョン管理 (TFVC) です。 この入門編は、Visual Studio for Mac で TFVC を使用する際の出発点としてご利用いただけます。

## <a name="requirements"></a>必要条件

* Visual Studio Community、Visual Studio Professional、Enterprise for Mac バージョン 7.5 以降。
* Azure DevOps Services、または Team Foundation Server 2013 以降。
* Team Foundation バージョン管理を使用するように設定された、Azure DevOps Services または Team Foundation Server のプロジェクト。

## <a name="installation"></a>インストール

Visual Studio for Mac でメニューから **[Visual Studio] > [拡張機能]** の順に選びます。 **[ギャラリー]** タブで **[バージョン管理] > [Team Foundation Version Control for TFS and VSTS]\(TFS と VSTS の Team Foundation バージョン管理\)** を選択し、**[インストール]** をクリックします。

![拡張機能マネージャー](media/tfvc-install.png)

画面の指示に従って、拡張機能をインストールします。 インストールした後、IDE を再起動します。

## <a name="updating-the-extension"></a>拡張機能の更新

TFVC 拡張機能への更新プログラムは、定期的に作成されます。 更新プログラムにアクセスするには、メニューから **[Visual Studio]、[拡張機能]** の順に選び、**[更新]** タブを選択します。リスト内の拡張機能を選択して、**[更新]** ボタンを押します。

![更新プログラムが表示されている拡張機能マネージャー](media/tfvc-update.png)

次のダイアログで **[インストール]** を押して古いパッケージをアンインストールし、新しいパッケージをインストールします。

各リリースの新着情報については、[リリース ノート](/visualstudio/releasenotes/vs2017-mac-preview-relnotes#team-foundation-version-control-extension--release-notes)に関するページを参照してください。

## <a name="using-the-add-in"></a>アドインの使用

拡張機能をインストールしたら、**[バージョン管理]、[TFS/Azure DevOps]、[Open from Remote Repository]\(リモート リポジトリから開く\)** メニュー項目の順に選択します。

![拡張機能を開くメニュー項目](media/tfvc-source-control-explorer-devops.png)

最初に VSTS または Team Foundation Server のいずれかを選択して、**[続行]** を押します。

![サーバーで接続する](media/tfvc-choose-server-type-devops.png)

### <a name="azure-repos-authentication"></a>Azure Repos の認証

Azure Repos でホストされているプロジェクトを選択すると、Microsoft アカウントの情報を入力する画面が表示されます。

![Azure Repos に接続する](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>TFS 認証

TFS に接続するには、サーバーの詳細とアカウントの資格情報を入力します。 NTLM 認証するドメインを入力します。それ以外の場合は、空白のままにして基本認証を使用します。 **[サーバーの追加]** を選択します。

![TFS Server にサインインする](media/tfvc-login.png)

## <a name="selecting-a-project"></a>プロジェクトの選択

認証が正常に行われると、**[Open from Source Control]\(ソース管理から開く\)** ダイアログでアカウントに関連付けられているリポジトリのリストを確認できます。

![プロジェクトを表示しているソース管理から開くダイアログ](media/tfvc-vsts-projects.png)

このダイアログは、次のノードで構成されています。

- Azure DevOps の組織またはコレクション: ログインに使用した Microsoft アカウントに接続されているすべての組織を表示します。
- プロジェクト: 各組織またはコレクションには、多くのプロジェクトを持つことができます。 プロジェクトは、ソース コード、作業項目、自動化されたビルドがホストされている場所です。

この時点で、プロジェクトまたは組織の名前で検索およびフィルター処理を行うことができます。

### <a name="adding-a-new-server"></a>新しいサーバーの追加

新しいサーバーをリストに追加するには、**[Open from Source Control]\(ソース管理から開く\)** ダイアログの **[ホストの追加]** ボタンを押します。

![新しいサーバーをリストに追加するための強調表示された追加ボタン](media/tfvc-add-new-server.png)

リストからプロバイダーを選択して、資格情報を入力します。

![ソース管理プロバイダー用のオプションを示すダイアログ](media/tfvc-add-new-creds-devops.png)

## <a name="creating-a-new-workspace"></a>新しいワークスペースの作成。

プロジェクトの操作を開始するには、_ワークスペース_が必要です。 まだワークスペースがない場合は、**[Open from Source Control]\(ソース管理から開く\)** ダイアログ内の **[ワークスペース]** コンボ ボックスからワークスペースを作成できます。

![新しいワークスペースの作成コンボ ボックスのオプション](media/tfvc-create-new-workspace.png)

新しいワークスペースの名前とローカル パスを設定して、**[ワークスペースの作成]** を選択します。

![新しいワークスペースの名前とローカル パスの入力](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>ソース コード エクスプローラーの使用

ワークスペースを作成してプロジェクトをマップしたら、_ソース コード エクスプローラー_の操作を開始できます。

ソース コード エクスプローラーを開くには、**[バージョン コントロール] > [TFS/Azure DevOps] > [ソース管理エクスプローラー]** の順にメニュー項目を選択します。

ソース コード エクスプローラーを使用すると、すべてのマップされているプロジェクト、そのファイルやフォルダー内を移動できます。 また、次のような基本のソース コントロール アクションをすべて実行することもできます。

- 最新バージョンの取得
- 特定バージョンの取得
- ファイルのチェックインとチェックアウト
- ファイルのロックとロック解除
- ファイルの追加、削除、名前の変更
- 履歴の表示
- 変更の比較。

これらのアクションの多くは、プロジェクトのコンテキスト アクションで使用できます。

![プロジェクトに対するコンテキスト メニューのアクション](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>ワークスペースの管理

「[新しいワークスペースの作成](#creating-a-new-workspace)」セクションで説明されたように、まだワークスペースを作成していない場合は、ソース コード エクスプローラーが空であることが表示されます。

![空のソース コード エクスプローラー](media/tfvc-setup-empty-sce.png)

ローカル ワークスペースを使ってリモート プロジェクトを設定するには、次の手順を使用します。

1. コンボ ボックスから**サーバー**を選択します。
1. "ワークスペースがありません" とローカル パスが "対応付けされていません" が示されていることに注意してください。 **[対応付けされていません]** リンクを選択して、**[新しいワークスペースの作成]** ダイアログを表示します。
1. ワークスペースの名前を入力し、**[Add Working Folder]\(作業フォルダーの追加\)** をクリックし、コンピューター上のローカル フォルダーにプロジェクトをマッピングします。

    ![既定のオプションを示している [新しいワークスペースの作成] ダイアログ](media/tfvc-workspace1.png)

1. "$" フォルダーを選択してサーバー上のすべてのプロジェクトを同じワークスペースにマッピングするか、個別のプロジェクトを選択して、**[OK]** をクリックします。

    ![すべてのプロジェクトを示している [フォルダーの参照] ダイアログ](media/tfvc-workspace2.png)

1. プロジェクトをマッピングするローカル コンピューター上の場所を選択して、**[フォルダーの選択]** をクリックします。
1. **[OK]** を押して、新しいワークスペースの詳細を確認します。

    ![追加された作業フォルダーを含む [新しいワークフローの追加] ダイアログ](media/tfvc-workspace3.png)

ワークスペースを設定したら、ソース コード エクスプローラーの **[ワークスペースの管理]** をクリックすることによって、変更または削除することができます。

![ワークスペースの管理](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>トラブルシューティング

### <a name="problems-using-basic-authentication"></a>基本認証の使用に関する問題

次のオプションを使用して、サーバーで認証できます。

- Oauth
- Basic
- Ntlm

基本認証を使用するには、以下の手順に従って、Azure DevOps Services で**代替認証資格情報**を有効にする必要があります。

1. 所有者として、Azure DevOps 組織にサインインします (https://dev.azure.com/{organization}/{project})。

2. 組織のツール バーの歯車アイコンを選択し、**[ポリシー]** を選択します。

    ![選択されたポリシー設定オプション](media/tfvc-auth2.png)

3. アプリケーションの接続設定を確認します。 セキュリティ ポリシーに基づいてこれらの設定を変更します。

    ![選択されたポリシー設定オプション](media/tfvc-auth.png)

### <a name="i-do-not-see-anything-in-tfvc"></a>TFVC に何も表示されない

開発用コンピューターに Team Foundation バージョン管理 (TFVC) を設定するには、「[ワークスペースの管理](#managing-workspaces)」セクションの説明に従って、ワークスペースを作成する**必要があります**。

ソース管理エクスプローラーで、**[ワークスペースの管理]** ボタンをクリックします。 手順に従って、開発用コンピューター上にあるフォルダーに、プロジェクトをマップします。

### <a name="i-do-not-see-any--all-of-my-projects"></a>一部/すべてのプロジェクトが表示されない

認証が済むと、プロジェクトの一覧が表示されるはずです。 既定では、TFS プロジェクトのみが表示されます。 他の種類のプロジェクトを表示するには、[See all projects]\(すべてのプロジェクトを表示する\) ボックスをオンにします。

適切な特権がない場合は、サーバー上にあるプロジェクトが表示されないことに注意してください。

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>次のような内容のエラーが表示される: "ワークスペースを作成できません。 もう一度お試しください"

[新しいワークスペースを作成](#creating-a-new-workspace)しようとするときは、次の条件が満たされていることを確認してください。

- ワークスペース名で無効な文字が使用されていない。
- 名前が 64 文字未満である。
- 他のワークスペースによってローカル パスが使用されていない。

## <a name="see-also"></a>関連項目

- [Visual Studio を使用して TFVC でコードを開発および共有する (Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)