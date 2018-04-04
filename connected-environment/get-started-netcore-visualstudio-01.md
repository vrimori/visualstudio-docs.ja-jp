---
title: クラウドで Kubernetes と Visual Studio を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 1 - ツールをインストールする | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: ghogen
ms.openlocfilehash: 4f25d4ae550f47533628bf073f2f22d9ed158cab
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Connected Environment で .NET Core と Visual Studio の使用を開始する

このガイドでは、以下の操作方法を学習します。

1. Azure で、開発用に最適化された Kubernetes ベースの環境を作成する。
1. Visual Studio を使用して、コンテナーでコードを繰り替えし開発する。
1. 2 つの別のサービスを個別に開発し、Kubernetes の DNS サービス探索を使用して別のサービスを呼び出す。
1. チーム環境でコードを生産的に開発してテストする。

[!INCLUDE[](includes/see-troubleshooting.md)]

## <a name="install-the-connected-environment-cli"></a>Connected Environment CLI をインストールする
Connected Environment には、最小限のローカル コンピューターのセットアップが必要です。 開発環境のほとんどの構成はクラウドに格納され、他のユーザーと共有することができます。

1. [Git for Windows](https://git-scm.com/downloads) をインストールして、既定のインストール オプションを選択します。 
1. [こちらのリンク](https://storage.googleapis.com/kubernetes-release/release/v1.9.0/bin/windows/amd64/kubectl.exe)から **kubectl.exe** をダウンロードして、パス上の場所に**保存**します。
1. [Connected Environment CLI インストーラー](https://aka.ms/get-vsce-windows)をダウンロードして、実行します。 

## <a name="get-kubernetes-debugging-tools"></a>Kubernetes デバッグ ツールを取得する
Connected Environment CLI をスタンドアロン ツールとして使用できますが、**VS Code** または **Visual Studio** を使用している .NET Core 開発者であれば、**Kubernetes デバッグ**などの豊富な機能を使用することができます。

### <a name="visual-studio-debugging"></a>Visual Studio デバッグ 
1. 最新バージョンの [Visual Studio 2017](https://www.visualstudio.com/vs/) をインストールします。
1. Visual Studio インストーラーで、次のワークロードが選択されていることを確認します。
    * ASP.NET と Web 開発
1. [Connected Environment 用の Visual Studio 拡張機能](https://aka.ms/get-vsce-visualstudio)をインストールします。

これで、Visual Studio を使用して ASP.NET Web アプリを作成する準備ができました。

> [!div class="nextstepaction"]
> [ASP.NET Web アプリを作成する](get-started-netcore-visualstudio-02.md)