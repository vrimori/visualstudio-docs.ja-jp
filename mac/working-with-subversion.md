---
title: "Subversion の使用 | Microsoft Docs"
description: "Visual Studio for Mac の Subversion を使用します。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: 026e3625b4ee2d6582ce5539e5cab68c945f09c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-subversion"></a>Subversion の使用

この記事で前に説明したように、Subversion は、集中管理されるデータの単一のマスター コピーをチェックアウトできるようにする集中管理されたバージョン コントロール システムです。 Git とは対照的に、Subversion リポジトリのチェックアウトではリポジトリ全体は複製されず、その時点のスナップショットのみを取得します。

Subversion では、コピー-変更-マージ モデルを使用して、ユーザーが同時に同じリポジトリで作業できるようにします。 これは、各ユーザーが、集中管理されているデータのローカルの作業コピーを作成し、それを独立して操作できることを意味します。 ユーザーの作業コピーへの変更は時系列的にマージされます。

たとえば、ユーザー A とユーザー B の両方がリモート リポジトリからコピーをチェックアウトし、それぞれファイルを変更するとします。 ユーザー A は、変更を終了し、それらをリモートでコミットします。 ユーザー B が作業をコミットする前に、リモートからの変更で作業コピーを更新することで、ユーザー A の変更をマージする必要があります。

以下のセクションでは、Visual Studio for Mac のバージョン コントロールに Subversion を使用する方法について説明します。

次の図は、Visual Studio for Mac の [バージョン コントロール] メニュー項目で提供されるオプションを示しています。

![[バージョン コントロール] メニュー項目](media/version-control-svnVersionControlMenu.png)

以下のセクションでは、各オプションの詳細を説明します。

## <a name="checkout"></a>チェックアウト

リモートの Subversion リポジトリの使用を始める前に、リポジトリをチェックアウトして、ローカル コンピューターにそのディレクトリのローカル コピー (または作業コピー) を作成する必要があります。

Visual Studio for Mac の**チェックアウト**機能の使用方法については、「[Setting up a Subversion repository](~/set-up-subversion-repository.md)」(Subversion リポジトリのセットアップ) の手順に従ってください。

## <a name="update-solution"></a>ソリューションの更新

リモート リポジトリを使用する場合は、他のユーザーがファイルを変更したために自分の作業コピーが古くなる可能性があることを覚えている必要があります。 これを予想して、作業を開始する前のコミットする前に、リポジトリからすべての変更をソリューションにプルすることを常にお勧めします。 これを行うには、*[バージョン コントロール] > [ソリューションの更新]* メニュー項目を選択します。

## <a name="review-solution-and-commit"></a>ソリューションの確認とコミット

ファイルの変更を確認するには、以下に示すように、各ドキュメントの [変更]、[変更履歴]、[ログ]、[マージ] タブを使用します。

![[バージョン コントロール] タブ](media/version-control-vcTabs.png)

**[バージョン コントロール] > [ソリューションの確認とコミット]** メニュー項目を参照して、プロジェクトのすべての変更を確認します。

![ソリューションの確認](media/version-control-vcStatus.png)

これにより、プロジェクトの各ファイルのすべての変更を表示し、[元に戻す]、[修正プログラムの作成]、[コミット] のオプション選択できます。

リモート リポジトリに対してファイルをコミットするには、[コミット] を押し、コミット メッセージを入力して、[コミット] ボタンで確認します。


![ファイルをコミットする](media/version-control-svnCommit.png)

これにより、変更がリポジトリに送信され、すべての変更の新しいリビジョンが作成されます。
