---
title: TF バージョン管理
description: Team Foundation バージョン管理で Team Foundation Server または Visual Studio Team Services に接続します。
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 58d0fc5c31b02574661f8b86a4ae8bcaf393be3a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693774"
---
# <a name="connecting-to-team-foundation-version-control"></a>Team Foundation バージョン管理に接続する 

> [!NOTE]
> **注**: 現在、Team Foundation バージョン管理サポートはプレビューとして提供されており、一部の機能は完全に動作していません。 [開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/41/index.html)で問題についてフィードバックしてください。 今後、さらに変更される予定です。

Visual Studio Team Services (VSTS) と Team Foundation Server (TFS) には、バージョン管理のモデルが 2 つあります。Git は分散型バージョン管理であり、Team Foundation バージョン管理 (TFVC) は集中型バージョン管理です。 この入門編は、Visual Studio for Mac で Team Foundation バージョン管理を使用する際の出発点としてご利用いただけます。

## <a name="requirements"></a>必要条件

* Visual Studio for Mac バージョン 7.5 以降。
* Visual Studio Team Services、または Team Foundation Server 2013 以降
* Team Foundation バージョン管理を使用するように設定された、Visual Studio Team Services または Team Foundation Server のプロジェクト。

## <a name="installation"></a>インストール

Visual Studio for Mac でメニューから **[Visual Studio] > [拡張機能]** の順に選びます。 **[ギャラリー]** タブで **[バージョン管理] > [Team Foundation Version Control for TFS and VSTS]\(TFS と VSTS の Team Foundation バージョン管理\)** を選択し、**[インストール]** をクリックします。

  ![拡張機能マネージャー](media/tfvc-install.png) 

画面の指示に従って、拡張機能をインストールします。 インストールした後、IDE を再起動します。

## <a name="using-the-add-in"></a>アドインの使用

拡張機能をインストールした後、**[バージョン管理] > [TFS/VSTS] > [Connect to Team Foundation Version Control...]\(Team Foundation バージョン管理に接続する...\)** メニュー項目を順に選択します。 **[追加]** をクリックして新しいアカウントを追加します。 

![TFVC Server を追加する](media/tfvc-add-remove-server.png)

最初に Visual Studio Team Services または Team Foundation Server を選択します。

![TFVC Server に接続する](media/tfvc-choose-server-type.png)

資格情報を入力して、**[ログイン]** をクリックします。 

![TFVC Server にログインする](media/tfvc-login.png)

正常にログインした後、アクセスするプロジェクトを選択して、**[OK]** をクリックします。 

![プロジェクトを選択する](media/tfvc-choose-projects.png)

**[バージョン管理] > [TFS/VSTS] > [ソース管理エクスプローラー]** メニュー項目を順に選択して、ソースを参照できるソース管理エクスプローラーを開きます。

> [!IMPORTANT]
> **既知の問題**: このプレビュー リリースでは、ソース管理エクスプローラーを初めて開いたとき、[新しいワークスペースを作成する](#creating-a-new-workspace)必要があります。

![ソース エクスプローラー](media/tfvc-source-explorer.png)

ソース コード エクスプローラーから、サーバーのソース コードを閲覧し、次の操作を実行できます。

- ワークスペースの管理 (作成、編集、削除)。
- プロジェクトの構造間の移動。
- プロジェクトのマッピング。
- プロジェクトの取得。
- ファイルのロックとロック解除。
- ファイルの名前変更。
- ファイルの削除。
- 新しいファイルの追加。
- チェックアウト。
- チェックイン。
- 変更履歴の表示。
- 変更の比較。

## <a name="creating-a-new-workspace"></a>新しいワークスペースの作成。

ソース管理エクスプローラーで、**[ワークスペースの管理]** ボタンをクリックします。 

![ワークスペースの管理](media/tfvc-manage-workspaces.png)

**[追加]** ボタンをクリックして、新しいワークスペースを作成します。

![ワークスペースの作成](media/tfvc-create-workspace.png)

ワークスペースの名前を入力し、**[Add Working Folder]\(作業フォルダーの追加\)** をクリックし、コンピューター上のローカル フォルダーにプロジェクトをマッピングします。

完了したら、**[OK]** をクリックし、[ワークスペースの管理] ダイアログを閉じます。 これでソース コード エクスプローラーからファイルを取得して開始できます。

## <a name="troubleshooting"></a>トラブルシューティング

### <a name="problems-using-basic-authentication"></a>基本認証の使用に関する問題

サーバーでの認証実行にはさまざまなオプションを使用できます。

- Oauth
- Basic
- Ntlm

基本認証を使用できるようにするには、以下の手順に従って、VSTS で **代替認証資格情報**を有効にする必要があります。

1. VSTS アカウントにアカウント所有者としてサインインします (https://{youraccount}.visualstudio.com)。
2. アカウント ツール バーの歯車アイコンを選択し、**[ポリシー]** を選択します。![選択されたポリシー設定オプション](media/tfvc-auth2.png) 
3. アプリケーションの接続設定を確認します。 セキュリティ ポリシーに基づいてこれらの設定を変更します。![選択されたポリシー設定オプション](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>TFVC に何も表示されない

開発用コンピューターに Team Foundation バージョン管理 (TFVC) を設定するには、「[新しいワークスペースの作成](#creating-a-new-workspace)」セクションの説明に従って、ワークスペースを作成する**必要があります**。

ソース管理エクスプローラーで、**[ワークスペースの管理]** ボタンをクリックします。 手順に従って、開発用コンピューター上にあるフォルダーに、チーム プロジェクトをマップします。

### <a name="i-do-not-see-any--all-of-my-projects"></a>一部/すべてのプロジェクトが表示されない

認証が済むと、プロジェクトの一覧が表示されるはずです。 既定では、TFS プロジェクトのみが表示されます。 他の種類のプロジェクトを表示するには、[See all projects]\(すべてのプロジェクトを表示する\) ボックスをオンにします。

適切な特権がない場合は、サーバー上にあるプロジェクトが表示されないことに注意してください。

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>次のような内容のエラーが表示される: "ワークスペースを作成できません。 もう一度お試しください"

[新しいワークスペースを作成](#creating-a-new-workspace)しようとするときは、次の条件が満たされていることを確認してください。

- ワークスペース名で無効な文字が使用されていない。
- 名前が 64 文字未満である。
- 他のワークスペースによってローカル パスが使用されていない。