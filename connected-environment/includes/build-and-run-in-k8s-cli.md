---
ms.topic: include
ms.openlocfilehash: b10d15b90f7f413d26adf8037c6f52c711a9ed69
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
ms.locfileid: "32030934"
---
## <a name="build-and-run-code-in-kubernetes"></a>Kubernetes でコードをビルドして実行する
それではコードを実行しましょう。 端末ウィンドウで、**ルート コード フォルダー**の webfrontend から次のコマンドを実行します。

```cmd
vsce up
```

コマンドの出力に注目してください。次のようなことに気付きます。
1. ソース コードは Azure の開発環境と同期します。
1. コード フォルダーで Docker アセットに指定されているように、コンテナー イメージが Azure でビルドされます。
1. コード フォルダーで Helm チャートに指定されているように、コンテナー イメージを活用する Kubernetes オブジェクトが作成されます。
1. コンテナーのエンドポイントに関する情報が表示されます。 今回はパブリック HTTPS URL が表示されるはずです。
1. 上記の段階が正常に完了していれば、コンテナーの起動時に `stdout` (および `stderr`) 出力が表示されるはずです。

> [!Note]
> 以上の手順は、`up` コマンドを初めて実行するときに時間がかかり、その後の実行ではもっと早く終わります。

## <a name="test-the-web-app"></a>Web アプリをテストする
コンソール出力を見て、`up` コマンドで作成されたパブリック URL に関する情報を探します。 次の形式になっています。 

`Running at public URL: https://<servicename>-<environmentname>.vsce.io` 

この URL をブラウザーで開きます。Web アプリ ロードが表示されるはずです。 コンテナーが実行されると、`stdout` と `stderr` の出力が端末ウィンドウに流れます。
