---
title: クラウドで Kubernetes を使用して、コンテナーを含む Node.js 開発環境を作成する - 手順 4 - Kubernetes でコンテナーをデバッグする | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: 2d1ec5fe0436b394083a247faa4519505aa21ceb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Connected Environment で Node.js の使用を開始する

前の手順: [Kubernetes で Node.js コンテナーを作成する](get-started-nodejs-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>VSCE デバッグ構成を選択する
1. デバッグ ビューを開くには、VS Code の横にある **[アクティビティ バー]** のデバッグ アイコンをクリックします。
1. アクティブ デバッグ構成として、**[Launch Program (VSCE)]\(プログラムの起動 (VSCE)\)** を選択します。

![](media/debug-configuration-nodejs.png)

> [!Note]
> コマンド パレットに Connected Environment コマンドが表示されない場合は、[Connected Environment 用の VS Code 拡張機能をインストールした](get-started-nodejs-01.md#get-kubernetes-debugging-for-vs-code)ことを確認してください。

## <a name="debug-the-container-in-kubernetes"></a>Kubernetes でコンテナーをデバッグする
**F5** キーを押して、Kubernetes でコードをデバッグします。

`up` コマンドの場合と同じように、デバッグの開始時にコードが開発環境に同期され、コンテナーがビルドされて Kubernetes に展開されます。 この場合も、もちろん、デバッガーはリモート コンテナーにアタッチされます。

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

サーバー側のコード ファイル (たとえば、`server.js` の `app.get('/api'...` 内) でブレークポイントを設定します。 ブラウザー ページを更新するか、[Say It Again]\(もう一度言ってください\) ボタンを押すと、ブレークポイントにヒットし、コードをステップ実行できます。

呼び出し履歴、ローカル変数、例外情報など、コードがローカルで実行される場合と同じように、デバッグ情報にフル アクセスできます。

## <a name="edit-code-and-refresh-the-debug-session"></a>コードを編集してデバッグ セッションを更新する
デバッガーをアクティブにして、コードを編集します。たとえば、hello メッセージをもう一度変更します。

```javascript
app.get('/api', function (req, res) {
    res.send('**** Hello from webfrontend running in Azure! ****');
});
```

ファイルを保存し、**デバッグ操作ウィンドウ**で **[更新]** ボタンをクリックします。 

![](media/debug-action-refresh-nodejs.png)

コードの編集ごとに新しいコンテナー イメージをリビルドして再展開する (これには、多くの場合、かなりの時間がかかります) のではなく、デバッグ セッションの間に Node.js プロセスを再開して、より高速な編集/デバッグ ループを提供します。

ブラウザーで Web アプリを更新するか、*[Say It Again]\(もう一度言ってください\)* ボタンを押します。 UI にはカスタム メッセージが表示されます。


## <a name="use-nodemon-to-develop-even-faster"></a>NodeMon を使用して開発をさらに高速化する
*nodemon* は、Node.js 開発者が迅速に開発を行うために使用する一般的なツールです。 サーバー側でコードを編集するたびに Node プロセスを手動で再開するのではなく、開発者は多くの場合、*nodemon* でファイルの変更を監視し、サーバー プロセスを自動的に再開するように Node プロジェクトを構成します。 このスタイルの作業では、開発者はコードの編集後にブラウザーを更新するだけです。

Connected Environment の目的は、ユーザーがローカルでの開発時に使用するものと同じ生産性の高い開発ワークフローを使用できるようにすることです。 これを示すために、サンプルの `webfrontend` プロジェクトは *nodemon* を使用するように構成されています (`package.json` では開発依存関係として構成されています)。

以下を試してみてください。
1. VS Code デバッガーを停止します。
1. VS Code の横にある **[アクティビティ バー]** のデバッグ アイコンをクリックします。 
1. アクティブ デバッグ構成として、**[Attach (VSCE)]\(アタッチ (VSCE)\)** を選択します。
1. F5 キーを押します。

この構成では、コンテナーは *nodemon* を開始するように構成されています。 サーバーのコードが編集されると、ローカルでの開発時の場合と同じように、*nodemon* は自動的に Node プロセスを再開します。 
1. `server.js` で hello メッセージをもう一度編集して、ファイルを保存します。
1. ブラウザーを更新するか、*[Say It Again]\(もう一度言ってください\)* ボタンをクリックして、変更が有効になっていることを確認します。

**これで、すばやくコードを反復処理し、Kubernetes で直接デバッグする方法がわかりました。** 次は、2 番目のコンテナーを作成して呼び出す方法を説明します。

> [!div class="nextstepaction"]
> [別のコンテナーで実行されているサービスを呼び出す](get-started-nodejs-05.md)

