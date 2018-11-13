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

この Hello World の例には、Visual Studio の初めての拡張機能の作成手順について説明します。 このチュートリアルでは、Visual Studio に新しいコマンドを追加する方法を示します。

プロセスでは、学習する方法。

* **[機能拡張プロジェクトを作成します。](#create-an-extensibility-project)**
* **[カスタム コマンドを追加します。](#add-a-custom-command)**
* **[ソース コードを変更します。](#modify-the-source-code)**
* **[実行します。](#run-it)**

この例で使用します (Visual C#)「と Hello World!」という名前のカスタム メニュー ボタンを追加するには 次に示します。

![Hello World コマンド](media/hello-world-say-hello-world.png)

> [!NOTE]
> この記事では、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac では、次を参照してください。[拡張機能のチュートリアルでは、Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough)します。

## <a name="prerequisites"></a>必須コンポーネント

開始する前にインストールされている確認、 **Visual Studio 拡張機能の開発**VSIX のテンプレートが必要し、サンプル コードを含むワークロード。

> [!NOTE]
> (Community、Professional、または Enterprise) Visual Studio 機能拡張プロジェクトを作成する Visual Studio の任意のエディションを使用することができます。

## <a name="create-an-extensibility-project"></a>機能拡張プロジェクトを作成します。

手順 1. **ファイル** メニューのをクリックして**新しいプロジェクト**します。 画面の下部には、プロジェクトの名前を入力します。

手順 2. **テンプレート** メニューのをクリックして**Visual c#**、 をクリックして**拡張**、 をクリックし、 **VSIX プロジェクト**。

![新しいプロジェクト](media/hello-world-new-project.png)

はじめに ページといくつかのサンプル リソースがわかります。

このチュートリアルのままにし、再度する必要がある場合で新しい HelloWorld プロジェクトを確認できます、**スタート ページ**で、**最近**セクション。

## <a name="add-a-custom-command"></a>カスタム コマンドを追加します。

手順 1. マニフェストを選択した場合、どのようなオプションは変更可能なインスタンス、メタデータ、説明、およびバージョンが確認できます。

手順 2. (ソリューションではなく) プロジェクトを右クリックします。 コンテキスト メニューで、次のようにクリックします。**追加**、 をクリックし、**新しい項目の**します。

手順 3. 選択、**拡張**セクションをクリックして**カスタム コマンド**します。

手順 4. **名前**下部にあるフィールドに、名前を付け、たとえば*Command.cs*します。

![カスタム コマンド](media/hello-world-custom-command.png)

新しいコマンドが記載**ソリューション エクスプ ローラー**下、**リソース**分岐します。 これは、PNG および ICO ファイル、イメージを変更する場合など、コマンドに関連するその他のファイルを検索します。

## <a name="modify-the-source-code"></a>ソース コードを変更します。

この時点では、追加するボタンが非常に汎用です。 変更を加える必要に応じて、VSCT ファイルおよび CS ファイルを変更する必要があります。

* VSCT ファイルは、することができます、コマンドの名前を変更として、Visual Studio のコマンドでは、どこを定義します。 VSCT ファイルを探索するときは、大量のコードのコントロールの各セクションで説明するコメントが付けられたコードが表示されます。

* CS ファイルでは、クリック ハンドラーなどのアクションを定義できます。

手順 1. **ソリューション エクスプ ローラー**、新しいコマンドの VSCT ファイルを検索します。 呼び出されるこの場合、 *CommandPackage.vsct*します。

![コマンドのパッケージ vsct](media/hello-world-command-package-vsct.png)

手順 2. 変更、`ButtonText`パラメーター`Say Hello World!`します。

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

手順 3. 戻り**ソリューション エクスプ ローラー**を見つけて、 *Command.cs*ファイル。 文字列を変更`message`コマンドの`string.Format(..)`に`Hello World!`します。

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

各ファイルに変更を保存してください。

## <a name="run-it"></a>実行します。

Visual Studio の実験用インスタンスでソース コードを実行できます。

手順 1. クリックして**開始**ツールバー。 プロジェクトがビルドされと呼ばれる Visual Studio の新しいインスタンスを起動するデバッガーを起動、**実験用インスタンス**します。

単語が表示されます**実験用インスタンス**Visual Studio タイトル バーにします。

![実験用インスタンスのタイトル バー](media/hello-world-exp-instance.png)

手順 2. **ツール**のメニュー、**実験用インスタンス**、 をクリックして**Say Hello World!** します。

![最終的な結果](media/hello-world-final-result.png)

新しいカスタム コマンドからの出力が表示されます、ここでは、画面の中央のダイアログ ボックスを提供する、 **Hello World!** メッセージが表示されます。

## <a name="next-steps"></a>次の手順

Visual Studio Extensibility の操作の基礎を理解できた次詳細についてここに示します。

* [Visual Studio 拡張機能の開発を始める](starting-to-develop-visual-studio-extensions.md)-サンプル、チュートリアル。 拡張機能を公開
* [新機能については、Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -Visual Studio 2017 での新しい拡張機能
* [Visual Studio SDK の内部](internals/inside-the-visual-studio-sdk.md)-Visual Studio 機能拡張の詳細を説明します。