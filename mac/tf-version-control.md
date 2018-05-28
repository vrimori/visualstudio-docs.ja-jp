---
title: TF バージョン管理
description: Team Foundation バージョン管理で Team Foundation Server または Visual Studio Team Services に接続します。
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: f892209faeb06ca703d28016457e9ba4ab86ccda
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
---
# <a name="connecting-to-team-foundation-version-control"></a>Team Foundation バージョン管理に接続する 

Visual Studio Team Services (VSTS) と Team Foundation Server (TFS) には、バージョン管理のモデルが 2 つあります。Git は分散型バージョン管理であり、Team Foundation バージョン管理 (TFVC) は集中型バージョン管理です。 この入門編は、Visual Studio for Mac で Team Foundation バージョン管理を使用する際の出発点としてご利用いただけます。

> [!NOTE]
> **注**: 現在、Team Foundation バージョン管理サポートはプレビューとして提供されており、一部の機能は完全に動作していません。 今後、さらに変更される予定です。

## <a name="requirements"></a>必要条件

* Visual Studio for Mac バージョン 7.5 以降。
* Visual Studio Team Server、または Team Foundation Server 2013 以降
* Team Foundation バージョン管理を使用するように設定された、Visual Studio Team Services または Team Foundation Server のプロジェクト。

## <a name="installation"></a>インストール

Visual Studio for Mac 内から、**[Visual Studio]、[拡張機能]** メニューの順に選択します。 "TF バージョン管理" を探し、**Team Foundation バージョン管理**拡張機能をインストールします。 再起動が要求されたら、IDE を再起動します。

## <a name="using-the-add-in"></a>アドインの使用

拡張機能がインストールされたら、**[バージョン管理]、[TFS/VSTS]、[Connect to Team Foundation Version Control...]\(Team Foundation バージョン管理に接続する...\)** メニューの順に選択します。 

![TFVC Server を追加する](media/tfvc-add-remove-server.png)


最初に Visual Studio Team Services または Team Foundation Server を選択します。

![TFVC Server に接続する](media/tfvc-choose-server-type.png)

資格情報を入力します。 

![TFVC Server にログインする](media/tfvc-login.png)

次に、アクセスするプロジェクトを選択します。 

![プロジェクトを選択する](media/tfvc-choose-projects.png)

続行するには、ダイアログを閉じ、**[バージョン管理]、[TFS/VSTS]、[ソース管理エクスプローラー]** メニューを使用してソースを閲覧します。

> [!WARNING]
> **既知の問題**: このプレビュー リリースでは、ソース管理エクスプローラーを初めて開いたとき、新しいワークスペースを作成する必要があります。

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

**[追加]** をクリックし、新しいワークスペースを作成します。

![ワークスペースの作成](media/tfvc-create-workspace.png)

ワークスペースの名前を入力し、**[Add Working Folder]\(作業フォルダーの追加\)** をクリックし、コンピューター上のローカル フォルダーにプロジェクトをマッピングします。

完了したら、**[OK]** をクリックし、[ワークスペースの管理] ダイアログを閉じます。 これでソース コード エクスプローラーからファイルを取得して開始できます。