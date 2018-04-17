---
title: クラウドで Kubernetes と Visual Studio を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 5 - 別のコンテナーを呼び出す | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: ghogen
ms.openlocfilehash: 8b0a0c78496b8f57764383d737e2a1cebb2dd6b9
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Connected Environment で .NET Core と Visual Studio の使用を開始する

前の手順: [Kubernetes でコンテナーをデバッグする](get-started-netcore-visualstudio-04.md)

## <a name="call-another-container"></a>別のコンテナーを呼び出す
このセクションでは、2 番目のサービス (`mywebapi`) を作成し、`webfrontend` で呼び出します。 各サービスは別のコンテナーで実行されます。 その後、両方のコンテナーでデバッグします。

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>*mywebapi* のサンプル コードをダウンロードする
時間の関係上、ここでは GitHub リポジトリからサンプル コードをダウンロードします。 https://github.com/Azure/vsce に移動し、**[Clone or Download]\(複製またはダウンロード\)** を選択して GitHub リポジトリをダウンロードします。 このセクションのコードは `vsce/samples/dotnetcore/getting-started/mywebapi` にあります。

## <a name="run-mywebapi"></a>*mywebapi* を実行する
1. *別の Visual Studio ウィンドウ*で `mywebapi` プロジェクトを開きます。
1. 前に `webfrontend` プロジェクトで行ったように、起動設定ドロップダウンから **[Connected Environment for AKS]** を選択します。 ここでは新しい開発環境を作成するのではなく、既に作成したものを選択します。 前述のように、[スペース] は既定の `mainline` のままにして、**[OK]** をクリックします。 [出力] ウィンドウを見ると、デバッグの開始時の作業速度を上げるために、開発環境でこの新しいサービスの "ウォーム アップ" が Visual Studio で開始されたことがわかります。
1. F5 キーを押して、サービスがビルドされ、展開されるのを待ちます。 Visual Studio のステータス バーがオレンジ色に変わると、準備ができたことがわかります。
1. **[出力]** ウィンドウの **[Connected Environment for AKS]** ウィンドウに表示されるエンドポイント URL (http://localhost:\<ポート番号\> など) をメモします。 コンテナーはローカルで実行されているように見えるかもしませんが、実際は Azure の開発環境で実行されています。
1. `mywebapi` の準備ができたら、ブラウザーで localhost アドレスを開き、`/api/values` を URL に追加して `ValuesController` の既定の GET API を呼び出します。 
1. すべての手順が正常に行われた場合、次のような `mywebapi` サービスからの応答を確認できます。

    ![](images/WebAPIResponse.png)

## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>*webfrontend* から *mywebapi* に対する要求を行う
次は、`mywebapi` に対する要求を行う `webfrontend` でコードを記述してみましょう。 `webfrontend` プロジェクトを持つ Visual Studio ウィンドウに切り替えます。 `HomeController.cs` ファイルで、About メソッドのコードを次のコードに*置き換え* ます。

 ```csharp
    public async Task<IActionResult> About()
    {
        ViewData["Message"] = "Hello from webfrontend";
        
        // Use HeaderPropagatingHttpClient instead of HttpClient so we can propagate
        // headers in the incoming request to any outgoing requests
        using (var client = new HeaderPropagatingHttpClient(this.Request))
        {
            // Call *mywebapi*, and display its response in the page
            var response = await client.GetAsync("http://mywebapi/api/values/1");
            ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
        }
    
        return View();
    }

```

`http://mywebapi` としてサービスを参照するために Kubernetes の DNS サービス探索がどのように使用されるのかに注目してください。 **この開発環境のコードは、運用環境で実行される場合と同じように実行されます**。

上記のコード例では、`HeaderPropagatingHttpClient` クラスも使用します。 このヘルパー クラスは、Connected Environment を使用するように構成したときにプロジェクトに追加された `HeaderPropagation.cs` ファイルです。 `HeaderPropagatingHttpClient` は既知の `HttpClient` クラスから派生したものであり、既存の ASP .NET HttpRequest オブジェクトから送信 HttpRequestMessage オブジェクトに特定のヘッダーを伝達する機能が追加されています。 これが、チーム シナリオでのより生産的な開発エクスペリエンスをどのように容易にするかについては、後で説明します。

## <a name="debug-across-multiple-services"></a>複数のサービスでデバッグする
1. この時点では、`mywebapi` はまだアタッチされたデバッガーで実行されているはずです。 そうでない場合は、`mywebapi` プロジェクトで F5 キーを押します。
1. `api/values/{id}` GET 要求を処理する、`ValuesController.cs` ファイルの `Get(int id)` メソッドでブレークポイントを設定します。
1. 上記のコードを貼り付けた `webfrontend` プロジェクトで、GET 要求を `mywebapi/api/values` に送信する直前にブレークポイントを設定します。
1. `webfrontend` プロジェクトで F5 キーを押します。 Visual Studio は適切な localhost ポートを再度ブラウザーで開き、Web アプリが表示されます。
1. ページの上部にある "**About**" リンクをクリックすると、`webfrontend` プロジェクトのブレークポイントがトリガーされます。 
1. F10 キーを押して続行します。 これで、`mywebapi` プロジェクトのブレークポイントがトリガーされます。
1. F5 キーを押して続行し、`webfrontend` プロジェクトのコードに戻ります。
1. F5 キーをもう一度押すと、要求が完了し、ブラウザーでページが返されます。 Web アプリの About ページには、2 つのサービスで連結されたメッセージ ("Hello from webfrontend and Hello from mywebapi") が表示されます。

お疲れさまでした。 これで、各コンテナーを個別に開発して展開できる、複数コンテナーのアプリケーションが用意できました。

> [!div class="nextstepaction"]
> [チーム開発について学習する](get-started-netcore-visualstudio-06.md)

