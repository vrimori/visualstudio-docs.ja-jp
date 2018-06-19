---
title: クラウドで Kubernetes を使用して、コンテナーを含む Node.js 開発環境を作成する - 手順 5 - 別のコンテナーを呼び出す | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: 89565869feec746aff75327b59ee7d0b466f26c1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31887506"
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Connected Environment で Node.js の使用を開始する

前の手順: [Kubernetes でコンテナーをデバッグする](get-started-nodejs-04.md)

このセクションでは、2 番目のサービス (`mywebapi`) を作成し、`webfrontend` で呼び出します。 各サービスは別のコンテナーで実行されます。 その後、両方のコンテナーでデバッグします。

![](media/multi-container.png)

## <a name="open-sample-code-for-mywebapi"></a>*mywebapi* のサンプル コードを開く
`vsce/samples` という名前のフォルダーの下に、このガイドの `mywebapi` のサンプル コードが既にあります (ない場合は、https://github.com/Azure/vsce に移動し、**[Clone or Download]\(複製またはダウンロード\)** を選択して GitHub リポジトリをダウンロードしてください)。このセクションのコードは `vsce/samples/nodejs/getting-started/mywebapi` にあります。

## <a name="run-mywebapi"></a>*mywebapi* を実行する
1. *別の VS Code ウィンドウ*で、`mywebapi` フォルダーを開きます。
1. F5 キーを押して、サービスがビルドされ、展開されるのを待ちます。 VS Code デバッグ バーが表示されると準備ができたことがわかります。
1. エンドポイント URL (http://localhost:\<ポート番号\> のように表示されます) をメモします。 **ヒント: VS Code ステータス バーにはクリック可能な URL が表示されます。** コンテナーはローカルで実行されているように見えるかもしませんが、実際は Azure の開発環境で実行されています。 localhost アドレスである理由は、`mywebapi` にパブリック エンドポイントが定義されておらず、Kubernetes インスタンス内からのみアクセス可能であるためです。 便宜上、また、ローカル コンピューターからのプライベート サービスとの対話を容易にするために、Connected Environment では、Azure で実行されているコンテナーへの一時的な SSH トンネルを作成します。
1. `mywebapi` の準備ができたら、ご利用のブラウザーで localhost アドレスを開きます。 `mywebapi` サービスからの応答 ("Hello from mywebapi") が表示されます。


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>*webfrontend* から *mywebapi* に対する要求を行う
次は、`mywebapi` に対する要求を行う `webfrontend` でコードを記述してみましょう。
1. `webfrontend` の VS Code ウィンドウに切り替えます。
1. `server.js` の先頭に次のコード行を追加します。
```javascript
var request = require('request');
var propagateHeaders = require('./propagateHeaders');
```

3. `/api` GET ハンドラーのコードを*置き換え* ます。 要求を処理する際に、`mywebapi` が順番に呼び出され、両方のサービスからの結果が返されます。

```javascript
app.get('/api', function (req, res) {
    request({
        uri: 'http://mywebapi',
        headers: propagateHeaders.from(req) // propagate headers to outgoing requests
    }, function (error, response, body) {
        res.send('Hello from webfrontend and ' + body);
    });
});
```

`http://mywebapi` としてサービスを参照するために Kubernetes の DNS サービス探索がどのように使用されるのかに注目してください。 **この開発環境のコードは、運用環境で実行される場合と同じように実行されます**。

上記のコード例では、`propagateHeaders` という名前のヘルパー モジュールが利用されています。 このヘルパーは、`vsce init` の実行時にコード フォルダーに追加されたものです。 `propagateHeaders.from()` 関数は、既存の http.IncomingMessage オブジェクトから送信要求のヘッダー プロジェクトに特定のヘッダーを伝達します。 これが、チーム シナリオでのより生産的な開発エクスペリエンスをどのように容易にするかについては、後で説明します。


## <a name="debug-across-multiple-services"></a>複数のサービスでデバッグする
1. この時点では、`mywebapi` はまだアタッチされたデバッガーで実行されているはずです。 そうでない場合は、`mywebapi` プロジェクトで F5 キーを押します。
1. 既定の GET `/` ハンドラーでブレークポイントを設定します。
1. `webfrontend` プロジェクトで、GET 要求を `http://mywebapi` に送信する直前にブレークポイントを設定します。
1. `webfrontend` プロジェクトで F5 キーを押します。
1. Web アプリを開き、両方のサービスでコードをステップ実行します。 Web アプリには、2 つのサービスで連結されたメッセージ ("Hello from webfrontend and Hello from mywebapi") が表示されます。


お疲れさまでした。 これで、各コンテナーを個別に開発して展開できる、複数コンテナーのアプリケーションが用意できました。

> [!div class="nextstepaction"]
> [チーム開発について学習する](get-started-nodejs-06.md)
