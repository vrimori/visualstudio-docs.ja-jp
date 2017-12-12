---
title: "Visual Studio for Mac での Subversion リポジトリのセットアップ | Microsoft Docs"
description: "Visual Studio for Mac で Git および Subversion を使用します。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: 0757ad29b8614a86f059f525f6ffe3100595d09b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="setting-up-a-subversion-repository"></a>Subversion リポジトリのセットアップ

Subversion は分散型のバージョン管理システムです。 これは、ユーザーが任意のファイルの任意のバージョンをチェックアウトできるすべてのファイルと変更履歴を含む、1 つのサーバーがあることを意味します。 ファイルがリモート Subversion レポジトリからチェックアウトされると、ユーザーはその時点のリポジトリのスナップショットを取得します。

Subversion の使用を開始する前に、Xcode コマンド ライン ツールをインストールする必要があります。これらのツールには適切な svn パッケージが含まれています。 次のコマンドを使用して、ターミナルに SVN がインストールされていることを確認できます。

`svn h`

1. オンラインで無料の SVN リポジトリを作成します。 この例では [Assembla](https://app.assembla.com/) が使用されています。 作成後に、URL が提供されます。これはリポジトリへの接続に使用されます。 

    ![SVN URL を取得してコピーする](media/version-control-subversion1-sml.png)

2. Visual Studio for Mac プロジェクトを開くか、作成します。

3. 次のように、プロジェクトを右クリックして、**[バージョン管理]、[Publish in Version Control...]\(バージョン管理で発行...\)** の順に選択します。 

    ![プロジェクトの発行を開始する](media/version-control-subversion2.png)

4. **[リポジトリへの接続]** タブで、上部のドロップダウンから **[Subversion]** を選択します。

5. 手順 1. の URL を入力します。 これで、他のフィールドが既定で設定されます。 

    ![[リポジトリの選択] と詳細入力ダイアログ](media/version-control-subversion3.png)

7. **[OK]** をクリックし、**[発行]** を押して確認します。

7. リポジトリを作成するサイトの資格情報の入力を求められる場合があります。 以下に示すように、これらを入力します。

    ![](media/version-control-subversion5.png)

8.  これで、使用可能なすべてのバージョン管理コマンドがバージョン管理メニューに表示されます。

