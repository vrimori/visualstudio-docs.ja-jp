---
title: Hello World |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c531d8acddfebcd2656d6dca05b95244f54ec01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="creating-your-first-extension-hello-world"></a>最初の拡張機能の作成: Hello World

この Hello World の例には、Visual Studio の最初の拡張機能の作成手順について説明します。 このチュートリアルでは、Visual Studio を新しいコマンドを追加する方法を示します。

プロセスでは学習する方法。

* **[機能拡張プロジェクトを作成します。](#create-an-extensibility-project)**
* **[カスタム コマンドを追加します。](#add-a-custom-command)**
* **[ソース コードを変更します。](#modify-the-source-code)**
* **[実行します。](#run-it)**

この例に使用する Visual C# でカスタム メニュー ボタン「言う Hello World!」という名前の追加 次のように検索するには。

![hello world コマンド](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>必須コンポーネント

作業を開始する前に、インストールされていることを確認してください、 **Visual Studio 拡張機能開発**ワークロードし、必要とするサンプル コードは、VSIX テンプレートが含まれます。

メモ: (Community、Professional、または Enterprise) Visual Studio 機能拡張プロジェクトを作成する Visual Studio の任意のバージョンを使用することができます。

## <a name="create-an-extensibility-project"></a>機能拡張プロジェクトを作成します。

手順 1. **ファイル** メニューをクリックして**新しいプロジェクト**です。 画面の下部にある、プロジェクトの名前を入力できます。

手順 2. **テンプレート** メニューのをクリックして**Visual c#**をクリックして**機能拡張**、順にクリック**VSIX プロジェクト**です。

![新しいプロジェクト](media/hello-world-new-project.png)

はじめに ページとサンプルの一部のリソースを閲覧する必要があります。

このチュートリアルのままにしてに戻る必要がある場合に新しい HelloWorld プロジェクトを見つけることができます、**スタート ページ**で、**最近使ったもの**セクションです。

## <a name="add-a-custom-command"></a>カスタム コマンドを追加します。

手順 1. マニフェストを選択した場合、どのようなオプションは変更できず、インスタンス、メタデータ、説明、およびバージョンが確認できます。

手順 2. プロジェクト (ソリューションではなく) を右クリックします。 コンテキスト メニューで、をクリックして**追加**、クリックして**ユーザー コントロール**です。

手順 3. 戻り、 **Extensibility**セクションで、クリックして**にカスタム コマンド**です。

手順 4. **名前**下部にあるフィールドに、Command.cs のインスタンスの名前を指定します。

![カスタム コマンド](media/hello-world-custom-command.png)

新しいコマンドが示されます、**ソリューション エクスプ ローラー**下にある、**リソース**分岐します。 PNG および ICO ファイル、イメージを変更する場合など、コマンドに関連するその他のファイルを調べることがもできます。

## <a name="modify-the-source-code"></a>ソース コードを変更します。

この時点で、ボタンを追加するは非常に一般的なです。 変更する場合に、VSCT ファイルおよび CS ファイルを変更する必要があります。

* VSCT ファイルは、場所をコマンドの名前を変更したりできるよう、Visual Studio コマンドのシステムでの移動先を定義します。 VSCT ファイルを探索するように、多くのコードは、制御の各セクションで説明するコメントが付けられたコードが表示されます。

* CS ファイルでは、クリック ハンドラーなどのアクションを定義することができます。

手順 1. **ソリューション エクスプ ローラー**、新しいコマンドの VSCT ファイルを検索します。 この場合、呼び出されます CommandPackage.vsct です。

![コマンド パッケージ vsct](media/hello-world-command-package-vsct.png)

手順 2. 変更、`ButtonText`に"Hello World!"のパラメーター

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

手順 3. 戻る**ソリューション エクスプ ローラー** Command.cs ファイルを検索します。 文字列を変更`message`コマンドの`string.Format(..)`"Hello World!"を

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

各ファイルに変更を保存することを確認してください。

## <a name="run-it"></a>実行します。

Visual Studio の実験用インスタンスで、ソース コードを実行できます。

手順 1. をクリックして**開始**ツールバー。 これは、プロジェクトをビルド デバッガーを開始と呼ばれる Visual Studio の新しいインスタンスを起動する、**実験用インスタンス**です。

Visual Studio タイトル バーに「実験用インスタンス」という語が表示されます。

![実験用インスタンスのタイトル バー](media/hello-world-exp-instance.png)

手順 2. **ツール**のメニューを開き、**実験用インスタンス**をクリックして**Say Hello World!**です。

![最終結果](media/hello-world-final-result.png)

この場合、センターでは、ダイアログは、"Hello World!"が表示される画面の新しいカスタムのコマンドからの出力が表示されます。 メッセージが表示されます。

## <a name="next-steps"></a>次の手順

Visual Studio 機能拡張の操作の基礎を理解したところで、詳細については、次に示します。

* [Visual Studio 拡張機能の開発を開始して](starting-to-develop-visual-studio-extensions.md)-サンプル、チュートリアルです。 拡張機能を公開します。
* [Visual Studio 2017 SDK の新](what-s-new-in-the-visual-studio-2017-sdk.md)-Visual Studio 2017 の新しい拡張機能
* [Visual Studio SDK 内](internals/inside-the-visual-studio-sdk.md)-Visual Studio 機能拡張の詳細