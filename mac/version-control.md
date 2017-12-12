---
title: "バージョン管理 | Microsoft Docs"
description: "Visual Studio for Mac で Git および Subversion を使用します。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 6e467cf6acda75948a189309b7648b1c4c085941
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="version-control"></a>バージョン管理

バージョン管理は、ファイルの多くの異なるバージョンを管理するためのシステムであり、ソフトウェア開発では、一般に多くの開発者が関与します。 バージョン管理システム (_VCS_) の主な目的は、すべてのユーザーがコードベースで同時に作業できるソリューションを見つけることです。

すべてのバージョン管理システムの中心にあるのは "_リポジトリ_" であり、リポジトリは、ファイル サーバーと同様に、すべての異なるファイルに対する中央データ ストアとして機能します。 ただし、ファイル サーバーとは異なり、リポジトリにはプロジェクトの履歴全体と行われたすべての改訂が含まれます。

リポジトリが中央のデータ ストアである場合、各ユーザーがデータのローカル ストアを保持して作業することが理にかなっています。 これは "_作業コピー_" と呼ばれます。 Visual Studio for Mac では、作業コピーはコンピューター上の他のローカル ディレクトリと同じように表示され、ファイルを読み取ったり書き込んだりすることができます。 ただし、Visual Studio for Mac にはバージョン管理システムが統合されているため、IDE を離れることなく Subversion や Git の機能を利用できます。

Subversion は分散型のバージョン管理システムです。 これは、ユーザーが任意のファイルの任意のバージョンをチェックアウトできるすべてのファイルと変更履歴を含む、1 つのサーバーがあることを意味します。 ファイルがリモート Subversion レポジトリからチェックアウトされると、ユーザーはその時点のリポジトリのスナップショットを取得します。

Git は、チームが同じドキュメントで同時に作業できるようにする分散型バージョン管理システムです。 つまり、すべてのファイルを含む 1 つのサーバーがありますが、この中央のソースからリポジトリがチェックアウトされるときには常に、リポジトリ全体がコンピューターにローカルで複製されます。

# <a name="basic-concepts"></a>基本的な概念 

Visual Studio for Mac は、Git と Subversion の両方のバージョン管理システムに対応しています。 Visual Studio for Mac で Git および Subversion のリポジトリをセットアップする方法、および変更のレビュー、コミット、プッシュなどの簡単な機能の説明については、以下の記事をご覧ください。

* [Git リポジトリのセットアップ](~/set-up-git-repository.md) 
* [Git の使用](~/working-with-git.md)
* [Subversion リポジトリのセットアップ](~/set-up-subversion-repository.md)
* [Subversion の使用](~/working-with-subversion.md)