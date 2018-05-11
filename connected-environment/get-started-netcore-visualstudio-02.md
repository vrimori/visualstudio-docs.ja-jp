---
title: クラウドで Kubernetes と Visual Studio を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 2 - ASP.NET Web アプリを作成する | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: d28661e8f252201a200c7e5f254d337edb6fe9e2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
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