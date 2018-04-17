---
title: クラウドで Kubernetes を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 3 - ASP.NET Core Web アプリを作成する | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: ghogen
ms.openlocfilehash: f858a013e4b0c2ce1c30b8f26f2dc33eebf19c27
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Connected Environment で .NET Core の使用を開始する

前の手順: [Azure で Kubernetes 開発環境を作成する](get-started-netcore-02.md)

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core Web アプリを作成する
[.NET Core](https://www.microsoft.com/net) がインストールされている場合は、`webfrontend` という名前のフォルダーで ASP.NET Core Web アプリをすばやく作成することができます。
```cmd
dotnet new mvc --name webfrontend
```

または、**GitHub からサンプル コードをダウンロード**します。その場合は、https://github.com/Azure/vsce に移動して、**[Clone or Download]\(複製またはダウンロード\)** を選択し、GitHub リポジトリをローカル環境にダウンロードします。 このガイドのコードは `vsce/samples/dotnetcore/getting-started/webfrontend` にあります。

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>コンテンツ ファイルを更新する
Connected Environment は Kubernetes で実行されているコードを取得するだけではありません。クラウドの Kubernetes 環境でコード変更が有効になっていることをすばやく繰り返し確認できるようにします。

1. `./Views/Home/Index.cshtml` ファイルを見つけて、HTML を編集します。 たとえば、`<h2>Application uses</h2>` と示されている 70 行目を `<h2>Hello k8s in Azure!</h2>` などに変更します。
1. ファイルを保存します。 その直後に、ターミナル ウィンドウに、実行中のコンテナー内のファイルが更新されたことを示すメッセージが表示されます。
1. ご利用のブラウザーに移動して、ページを更新します。 更新された HTML は Web ページに表示されます。

どうなっているのでしょうか。 HTML や CSS などのコンテンツ ファイルの編集には、.NET Core Web アプリでの再コンパイルは必要ありません。したがって、アクティブな `vsce up` コマンドで変更されたコンテンツ ファイルが Azure で実行中のコンテナーに自動的に同期されるため、コンテンツの編集をすぐに確認できます。

## <a name="update-a-code-file"></a>コード ファイルを更新する
.NET Core アプリでは更新されたアプリケーション バイナリを再ビルドして生成する必要があるため、コード ファイルの更新にはもう少し作業が必要です。

1. ターミナル ウィンドウで、`Ctrl+C` を押します (これで `vsce up` が停止します)。
1. `Controllers/HomeController.cs` という名前のコード ファイルを開き、About ページに表示されるメッセージ (`ViewData["Message"] = "Your application description page.";`) を編集します。
1. ファイルを保存します。
1. ターミナル ウィンドウで `vsce up` を実行します。 

これにより、コンテナー イメージがリビルドされ、Helm チャートが再展開されます。 実行中のアプリケーションでコード変更が有効になったことを確認するには、Web アプリで About メニューに移動します。


ただし、コードを開発する*さらに速い方法*もあります。これについては、次のセクションで説明します。 
> [!div class="nextstepaction"]
> [Kubernetes でコンテナーをデバッグする](get-started-netcore-04.md)

