---
title: クラウドで Kubernetes と Visual Studio を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 4 - Kubernetes でコンテナーをデバッグする | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: 75588fcabbba739c4670da42e24665428ff89130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Connected Environment で .NET Core と Visual Studio の使用を開始する

前の手順: [Azure で開発環境を作成する](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>Kubernetes でコンテナーをデバッグする
開発環境が正常に作成されたら、アプリケーションをデバッグすることができます。 コードでブレークポイントを設定します。たとえば、`Message` 変数を設定する `HomeController.cs` ファイルの 20 行目に設定します。 **F5** キーを押して、デバッグを開始します。 

Visual Studio は環境開発と通信し、アプリケーションをビルドして展開してから、実行されている Web アプリでブラウザーを開きます。 コンテナーはローカルで実行されているように見えるかもしませんが、実際は Azure の開発環境で実行されています。 localhost アドレスである理由は、Connected Environment では Azure で実行されているコンテナーに一時的な SSH トンネルが作成されるためです。

ページの上部にある "**About**" リンクをクリックすると、ブレークポイントがトリガーされます。 呼び出し履歴、ローカル変数、例外情報など、コードがローカルで実行される場合と同じように、デバッグ情報にフル アクセスできます。

> [!div class="nextstepaction"]
> [別のコンテナーを呼び出す](get-started-netcore-visualstudio-05.md)