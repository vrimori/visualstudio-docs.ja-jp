---
title: クラウドで Kubernetes と Visual Studio を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 2 - ASP.NET Web アプリを作成する | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: ghogen
ms.openlocfilehash: 3f60fc076d7b42a3c667455b5474572ed7e22991
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Connected Environment で .NET Core と Visual Studio の使用を開始する

前の手順: [ツールをインストールする](get-started-netcore-visualstudio-01.md)

## <a name="create-an-aspnet-web-app"></a>ASP.NET Web アプリを作成する
Visual Studio 2017 内から、新しいプロジェクトを作成します。現時点では、これは **ASP.NET Core Web アプリケーション**である必要があります。 プロジェクトに '**webfrontend**' という名前を付けます。

![](images/NewProjectDialog1.png)

**[Web アプリケーション (モデル ビュー コントローラー)]** テンプレートを選択し、ダイアログ上部の 2 つのドロップダウンで **.NET Core** と **ASP.NET Core 2.0** が対象になっていることを確認します。 **[OK]** をクリックして、プロジェクトを作成します。

![](images/NewProjectDialog2.png)

> [!div class="nextstepaction"]
> [Azure で開発環境を作成する](get-started-netcore-visualstudio-03.md)