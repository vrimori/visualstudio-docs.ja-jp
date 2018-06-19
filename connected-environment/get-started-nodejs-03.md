---
title: クラウドで Kubernetes を使用して、コンテナーを含む Node.js 開発環境を作成する - 手順 3 - ASP.NET Web アプリを作成する | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: 34e1f07e173ccba6aab561fb4795abbe938e0127
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31890155"
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Connected Environment で Node.js の使用を開始する

前の手順: [Azure で Kubernetes 開発環境を作成する](get-started-nodejs-02.md)

## <a name="create-a-nodejs-web-app"></a>Node.js Web アプリを作成する
GitHub からコードをダウンロードします。その場合、https://github.com/Azure/vsce に移動して、**[Clone or Download]\(複製またはダウンロード\)** を選択し、GitHub リポジトリをローカル環境にダウンロードします。 このガイドのコードは `vsce/samples/nodejs/getting-started/webfrontend` にあります。

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>コンテンツ ファイルを更新する
Connected Environment は Kubernetes で実行されているコードを取得するだけではありません。クラウドの Kubernetes 環境でコード変更が有効になっていることをすばやく繰り返し確認できるようにします。

1. `./public/index.html` ファイルを見つけて、HTML を編集します。 たとえば、次のように、ページの背景色を青色の網掛けに変更します。

```html
<body style="background-color: #95B9C7; margin-left:10px; margin-right:10px;">
```

2. ファイルを保存します。 その直後に、ターミナル ウィンドウに、実行中のコンテナー内のファイルが更新されたことを示すメッセージが表示されます。
1. ご利用のブラウザーに移動して、ページを更新します。 色は更新されています。

どうなっているのでしょうか。 HTML や CSS などのコンテンツ ファイルの編集には、Node.js プロセスを再開する必要はありません。したがって、アクティブな `vsce up` コマンドで変更されたコンテンツ ファイルが Azure で実行中のコンテナーに自動的に同期されるため、コンテンツの編集をすぐに確認できます。

### <a name="test-from-a-mobile-device"></a>モバイル デバイスからテストする
モバイル デバイスで Web アプリを開くと、小さなデバイスでは UI が正しく表示されないことがわかります。

これを解決するには、次のように `viewport` メタ タグを追加します。
1. `./public/index.html` ファイルを開きます。
1. 次のように、既存の `head` 要素に `viewport` メタ タグを追加します。

```html
<head>
    <!-- Add this line -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

1. ファイルを保存します。
1. デバイスのブラウザーを更新します。 これで、Web アプリが正しくレンダリングされたことがわかります。 

これは、アプリを使用するためにデバイスでテストするまで見つからない一部の問題のみを示す例です。 VS Connected Environment では、コードをすばやく反復処理し、ターゲット デバイスでの変更を検証できます。

## <a name="update-a-code-file"></a>コード ファイルを更新する
Node.js アプリを再起動する必要があるため、サーバー側のコード ファイルの更新にはもう少し作業が必要です。

1. ターミナル ウィンドウで、`Ctrl+C` を押します (これで `vsce up` が停止します)。
1. `server.js` という名前のコード ファイルを開き、次のようにサービスの hello メッセージを編集します。 

```javascript
res.send('Hello from webfrontend running in Azure!');
```

3. ファイルを保存します。
1. ターミナル ウィンドウで `vsce up` を実行します。 

これにより、コンテナー イメージがリビルドされ、Helm チャートが再展開されます。 ブラウザー ページを再度読み込んで、コードの変更が有効になっていることを確認します。


ただし、コードを開発する*さらに速い方法*もあります。これについては、次のセクションで説明します。 
> [!div class="nextstepaction"]
> [Kubernetes でコンテナーをデバッグする](get-started-nodejs-04.md)
