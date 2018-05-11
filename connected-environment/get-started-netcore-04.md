---
title: クラウドで Kubernetes を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 4 - Kubernetes でコンテナーをデバッグする | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: 043052dec78251647a3ef12e0b612355b6334692
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Connected Environment で .NET Core の使用を開始する
 
前の手順: [ASP.NET Core Web アプリを作成する](get-started-netcore-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>VSCE デバッグ構成を選択する
1. デバッグ ビューを開くには、VS Code の横にある **[アクティビティ バー]** のデバッグ アイコンをクリックします。
1. アクティブ デバッグ構成として、**[.NET Core Launch (VSCE)]** を選択します。

![](media/debug-configuration.png)

> [!Note]
> コマンド パレットに Connected Environment コマンドが表示されない場合は、[Connected Environment 用の VS Code 拡張機能をインストールした](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code)ことを確認してください。


## <a name="debug-the-container-in-kubernetes"></a>Kubernetes でコンテナーをデバッグする
**F5** キーを押して、Kubernetes でコードをデバッグします。

`up` コマンドの場合と同じように、コードが開発環境に同期され、コンテナーがビルドされて Kubernetes に展開されます。 この場合も、もちろん、デバッガーはリモート コンテナーにアタッチされます。

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

サーバー側のコード ファイル (たとえば、`Controllers/HomeController.cs` ソース ファイルの `Index()` 関数内) でブレークポイントを設定します。 ブラウザー ページを更新すると、ブレークポイントにヒットします。

呼び出し履歴、ローカル変数、例外情報など、コードがローカルで実行される場合と同じように、デバッグ情報にフル アクセスできます。

## <a name="edit-code-and-refresh"></a>コードを編集して更新する
デバッガーをアクティブにして、コードを編集します。 たとえば、`Controllers/HomeController.cs` で About ページのメッセージを変更します。 

```csharp
public IActionResult About()
{
    ViewData["Message"] = "My custom message in the About page.";
    return View();
}
```

ファイルを保存し、**デバッグ操作ウィンドウ**で **[更新]** ボタンをクリックします。 

![](media/debug-action-refresh.png)

コードの編集ごとに新しいコンテナー イメージをリビルドして再展開する (これには、多くの場合、かなりの時間がかかります) のではなく、Connected Environment は既存のコンテナー内のコードを 1 つずつ再コンパイルしてより高速な編集/デバッグ ループを提供します。

ブラウザーで Web アプリを更新して、About ページに移動します。 UI にはカスタム メッセージが表示されます。

**これで、すばやくコードを反復処理し、Kubernetes で直接デバッグする方法がわかりました。** 次は、2 番目のコンテナーを作成して呼び出す方法を説明します。

> [!div class="nextstepaction"]
> [別のコンテナーで実行されているサービスを呼び出す](get-started-netcore-05.md)
