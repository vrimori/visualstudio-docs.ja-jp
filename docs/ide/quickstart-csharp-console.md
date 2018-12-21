---
title: Visual Studio を使用して初めての C# コンソール アプリを作成する
titleSuffix: ''
description: Visual Studio で C# を使用して、シンプルな Hello World コンソール アプリを作成する方法について、ステップ バイ ステップで説明します。
ms.date: 09/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.custom: seodec18
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a1d7b165466f686549273394c204e4ab31c06b46
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158607"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>クイック スタート: Visual Studio を使用して初めての C# コンソール アプリを作成する

ここでは 5 分から 10 分で Visual Studio 統合開発環境 (IDE) の概要を示し、コンソールで実行される簡単な C# アプリを作成します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、C# アプリケーション プロジェクトを作成します。 このプロジェクトの種類には、必要となるすべてのテンプレート ファイルが付属していますので、何も追加する必要はありません。

1. Visual Studio 2017 を開きます。

2. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

3. 左側のウィンドウの **[新しいプロジェクト]** ダイアログ ボックスで、**[C#]** を展開し、**[.NET Core]** を選択します。 中央のウィンドウで、**[Console App (.NET Core)]** を選択します。 プロジェクトに *HelloWorld* という名前を付けます。

   ![Visual Studio IDE の [新しいプロジェクト] ダイアログ ボックスに示されているコンソール アプリ (.NET Core) プロジェクト テンプレート](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     **[Console App (.NET Core)]** プロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクを選択します。

   ![[新しいプロジェクト] ダイアログ ボックスから [Visual Studio インストーラーを開く] リンクを選択する](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Visual Studio インストーラーが起動します。 **[.NET Core クロスプラットフォームの開発]** ワークロードを選択し、**[変更]** を選択します。

     ![Visual Studio インストーラーの [.NET Core クロスプラットフォームの開発] ワークロード](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>アプリケーションを作成する

C# プロジェクト テンプレートを選択し、プロジェクトに名前を付けると、簡単な "Hello World" アプリケーションが Visual Studio によって自動的に作成されます。 

(これを行うために、<xref:System.Console.WriteLine%2A> メソッドが呼び出され、リテラル文字列 "Hello World!" が コンソール ウィンドウに表示されます。)

   ![テンプレートから既定の Hello World コードを表示する](../ide/media/csharp-console-helloworld-template.png)

**F5** キーを押すと、プログラムをデバッグ モードで実行できます。 しかし、コンソール ウィンドウが表示されるのは、閉じる前の一瞬だけです。

(これは、1 つのステートメントを実行すると `Main` メソッドが終了し、アプリケーションも終了するためです。)

### <a name="add-some-code"></a>何らかのコードを追加する

アプリケーションを一時停止させるコードを追加して、**ENTER** キーを押すまではコンソール ウィンドウが閉じられないようにしましょう。

1. <xref:System.Console.WriteLine%2A> メソッドへの呼び出しのすぐ後に、次のコードを追加します。

   ```csharp
   Console.ReadLine();
   ```

1. コード エディターで次ようになっていることを確認します。

   ![Hello World アプリを一時停止させるコードを追加する](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>アプリケーションの実行

1. ツールバーの **HelloWorld** ボタンを選択して、デバッグ モードでアプリケーションを実行します。 (または、**F5** キーを押します。)

   ![[Hello World] ボタンを選択して、ツールバーからアプリを実行する](../ide/media/csharp-console-hello-world-button.png)

1. コンソール ウィンドウでアプリを確認します。

   ![Hello World! が表示されたコンソール ウィンドウ](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>アプリケーションを終了する

1. **ENTER** キーを押して、コンソール ウィンドウを閉じます。

1. Visual Studio の **[出力]** ウィンドウを閉じます。

   ![Visual Studio の [出力] ウィンドウを閉じる](../ide/media/csharp-hello-world-close-output-pane.png)

1. Visual Studio を閉じます。

## <a name="next-steps"></a>次の手順

このクイック スタートは完了しました。 C# と Visual Studio IDE について、少しはご理解いただけたかと思います。 詳細については、引き続き以下のチュートリアルをご覧ください。

> [!div class="nextstepaction"]
> [Visual Studio での C# コンソール アプリの概要](tutorial-csharp-console.md)
