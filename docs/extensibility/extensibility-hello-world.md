---
title: Hello World の拡張機能のチュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2122a98778372690990a75269be2f3087653678
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349466"
---
# <a name="create-your-first-extension-hello-world"></a>初めての拡張機能の作成: Hello World

この Hello World の例では、Visual Studio の初めての拡張機能の作成手順について説明します。 このチュートリアルでは、Visual Studio に新しいコマンドを追加する方法を示します。

学習方法は以下の手順となります。

* **[機能拡張プロジェクトを作成します。](#create-an-extensibility-project)**
* **[カスタム コマンドを追加します。](#add-a-custom-command)**
* **[ソース コードを変更します。](#modify-the-source-code)**
* **[実行します。](#run-it)**

この例で使用します (Visual C#)「と Hello World!」という名前のカスタム メニュー ボタンを追加するには 次に示します。

![Hello World コマンド](media/hello-world-say-hello-world.png)

> [!NOTE]
> この記事では、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac では、次を参照してください。[拡張機能のチュートリアルでは、Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough)します。

## <a name="prerequisites"></a>必須コンポーネント

開始する前に、 必要なVSIX のテンプレートとサンプル コードを含む**Visual Studio 拡張機能の開発**ワークロードがインストールされていることを確認してください。

> [!NOTE]
> Visual Studio 機能拡張プロジェクトを作成するには、Visual Studio の任意のエディション(Community、Professional、または Enterprise)を使用することができます。

## <a name="create-an-extensibility-project"></a>機能拡張プロジェクトの作成

手順 1. **ファイル** メニューのをクリックして**新しいプロジェクト**します。 画面の下部には、プロジェクトの名前を入力します。

手順 2. **テンプレート** メニューのをクリックして**Visual c#**、 をクリックして**拡張**、 をクリックし、 **VSIX プロジェクト**。

![新しいプロジェクト](media/hello-world-new-project.png)

はじめに ページといくつかのサンプル リソースがわかります。

このチュートリアルを終了した後に再開する必要がある場合、 **スタート ページ** の **最近** セクションで HelloWorld プロジェクトを見つけられます。

## <a name="add-a-custom-command"></a>カスタム コマンドの追加

手順 1. マニフェストファイルを選択した場合、インスタンス、メタデータ、説明、およびバージョンのどのオプションが変更可能か確認できます。

手順 2. (ソリューションではなく) プロジェクトを右クリックします。 コンテキスト メニューで、次のようにクリックします。**追加**、 をクリックし、**新しい項目の**します。

手順 3. **Extensibility**セクションを選択し、**Custom Command**をクリックします。

手順 4. 下部にある**名前**フィールドに、たとえば *Command.cs* のような名前を付けます。

![カスタム コマンド](media/hello-world-custom-command.png)

新しいコマンドは**ソリューション エクスプローラー**の**リソース**フォルダに表示されます。 これは、PNG および ICO ファイルのようなイメージを変更する場合など、コマンドに関連するその他のファイルが見つかります。

## <a name="modify-the-source-code"></a>ソース コードの変更

この時点では、追加されたボタンはとても一般的な状態になっています。 変更したい場合は、VSCT ファイルおよび CS ファイルを修正する必要があります。

* VSCT ファイルはコマンドの名前の変更だけでなく、Visual Studioのコマンドシステムでの場所を定義します。 VSCT ファイルを探索するときは、それぞれのコードが制御しているセクションが何であるかの説明のコメントが大量に付けられていることが判ります。

* CS ファイルでは、クリック ハンドラーなどのアクションを定義できます。

手順 1. **ソリューション エクスプローラー**内で新規作成したコマンドの VSCT ファイルを検索します。 今回の場合は*CommandPackage.vsct*となっています。

![コマンドのパッケージ vsct](media/hello-world-command-package-vsct.png)

手順 2. `ButtonText`パラメーターを`Say Hello World!`に変更します。

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

手順 3. **ソリューション エクスプ ローラー**に戻って、*Command.cs*ファイルを探します。 文字列型変数`message`の処理を`string.Format(..)`から`Hello World!`に変更します。

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

各ファイルの変更が保存されているか確認してください。

## <a name="run-it"></a>実行

Visual Studio の実験用インスタンスでソース コードを実行できます。

手順 1. ツールバーの**デバッグの開始**をクリックします。 プロジェクトがビルドされ、**実験的なインスタンス**と呼ばれるVisual Studio の新しいインスタンスが起動されてデバッグが開始されます。

Visual Studioのタイトル バーには**実験的なインスタンス**と表示されます。

![実験的なインスタンスのタイトル バー](media/hello-world-exp-instance.png)

手順 2. **ツール**のメニュー、**実験用インスタンス**、 をクリックして**Say Hello World!** します。

![最終的な結果](media/hello-world-final-result.png)

新規作成したカスタム コマンドからの出力、この場合では画面の中央のダイアログ ボックスに **Hello World!** メッセージが表示されます。

## <a name="next-steps"></a>次の手順

Visual Studio 拡張機能 の作業の基礎を知ることができたので、以下でさらに学習ができます。

* [Visual Studio 拡張機能の開発を始める](starting-to-develop-visual-studio-extensions.md)-サンプル、チュートリアル。 拡張機能を公開
* [新機能については、Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -Visual Studio 2017 での新しい拡張機能
* [Visual Studio SDK の内部](internals/inside-the-visual-studio-sdk.md)-Visual Studio 機能拡張の詳細を説明します。