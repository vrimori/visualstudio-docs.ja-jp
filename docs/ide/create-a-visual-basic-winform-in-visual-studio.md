---
title: Visual Basic を使用して Windows フォーム アプリを作成する
description: Visual Studio で Visual Basic を使用して Windows フォーム アプリを作成する方法の詳細な手順を説明します。
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 6cdc059b224508d28b43c05fac1b8d5befc15564
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690425"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Visual Studio で Visual Basic を使用して Windows フォーム アプリを作成する

ここでは、Visual Studio 統合開発環境 (IDE) の概要を示し、Windows ベースのユーザー インターフェイス (UI) を備えた簡単な Visual Basic アプリケーションを作成します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、Visual Basic アプリケーション プロジェクトを作成します。 このプロジェクトの種類には、必要とするすべてのテンプレート ファイルが付属していますので、何も追加する必要はありません。

1. Visual Studio 2017 を開きます。

2. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

3. 左側のウィンドウの **[新しいプロジェクト]** ダイアログ ボックスで、**[Visual Basic]** を展開し、**[Windows デスクトップ]** を選択します。 中央のウィンドウで、**[Windows フォーム アプリケーション (.NET Framework)]** を選択します。 ファイルに `HelloWorld` という名前を付けます。

     **[Windows フォーム アプリケーション (.NET Framework)]** プロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスを取り消し、上部のメニュー バーで **[ツール]** > **[ツールと機能を取得]** の順に選択します。 Visual Studio インストーラーが起動します。 **.NET デスクトップ開発**ワークロードを選択し、**[変更]** を選択します。

     ![Visual Studio インストーラーの .NET Core ワークロード](../ide/media/install-dot-net-desktop-env.png)

## <a name="create-the-application"></a>アプリケーションを作成する

Visual Basic プロジェクト テンプレートを選択し、ファイルに名前を付けると、Visual Studio によって目的のフォームが開かれます。 フォームは、Windows ユーザー インターフェイスです。 このフォームにコントロールを追加して "Hello World" アプリケーションを作成し、このアプリケーションを実行します。

### <a name="add-a-button-to-the-form"></a>フォームにボタンを追加する

1. **[ツールボックス]** をクリックして、ツールボックスのスライド アウト ウィンドウを開きます 

     ![[ツールボックス] をクリックして [ツールボックス] ウィンドウを開く](../ide/media/vb-toolbox-toolwindow.png)

     (**ツールボックス**のスライド アウト オプションが表示されない場合は、メニュー バーから開くことができます。 そのためには、**[ビュー]** > **[ツールボックス]** をクリックします。 または、**Ctrl**+**Alt**+**X** キーを押します)。

2. **[ピン設定]** アイコンをクリックして、**[ツールボックス]** ウィンドウをドッキングします。

     ![[ツールボックス] ウィンドウを IDE にピン留めする [ピン設定] アイコンをクリックします。](../ide/media/vb-pin-the-toolbox-window.png)
3. **[ボタン]** コントロールをクリックし、フォームまでドラッグします。

     ![フォームにボタンを追加する](../ide/media/vb-add-a-button-to-form1.png)

4. **[プロパティ]** ウィンドウの **[外観]** セクションで、`Click this` と入力し、**Enter** キーを押します。

     ![フォーム上のボタンにテキストを追加する](../ide/media/vb-button-control-text.png)

     (**[プロパティ]** ウィンドウが表示されない場合は、メニュー バーから開くことができます。 そのためには、**[表示]** > **[プロパティ ウィンドウ]** をクリックします。 または **F4** キーを押します)。

5. **[プロパティ]** ウィンドウの **[デザイン]** セクションで、名前を **Button1** から `btnClickThis` に変更し、**Enter** キーを押します。

     ![フォーム上のボタンに関数を追加する](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>フォームにラベルを追加する

アクションを作成するボタン コントロールが追加されましたので、次にテキストが送信されるラベル コントロールを追加してみましょう。

1. **[ツールボックス]** ウィンドウから **[ラベル]** コントロールを選択し、そのラベルをフォームにドラッグし、**[Click this]** ボタンの下にドロップします。

2. **[プロパティ]** ウィンドウの **[デザイン]** セクションで、名前を **Label1** から `lblHelloWorld` に変更し、**Enter** キーを押します。

### <a name="add-code-to-the-form"></a>フォームにコードを追加する

1. **[Form1.vb [Design]]** ウィンドウで、**[Click this]** ボタンをダブルクリックして、**[Form1.vb]** ウィンドウを開きます 

      (あるいは、**[ソリューション エクスプローラー]** で **[Form1.vb]** を展開し、**[Form1]** をクリックします)。

2. **[Form1.vb]** ウィンドウの **Private Sub** 行と **End Sub** 行の間に、「`lblHelloWorld.Text = "Hello World!"`」と入力するか、貼り付けます。

     ![フォームにコードを追加する](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>アプリケーションの実行

1. **[開始]** ボタンをクリックしてアプリケーションを実行します。

     ![[開始] をクリックして、アプリをデバッグして実行する](../ide/media/vb-click-start-hello-world.png)

   いくつかの処理が行われます。 Visual Studio IDE 内では、**[診断ツール]** ウィンドウが開き、**[出力]** ウィンドウも開きます。 ただし、IDE の外部では、**[Form1]** ダイアログ ボックスが表示されます。 このダイアログ ボックスには、**[Click this]** ボタンと **Label1** というテキストが表示されます。

2. **[Form1]** ダイアログ ボックスの **[Click this]** ボタンをクリックします。 テキスト **Label1** が **Hello World!** に変更されることがわかります。

    ![テキスト Label1 を含む [Form1] ダイアログ ボックス ](../ide/media/vb-form1-dialog-hello-world.png)

このクイック スタートは完了しました。 Visual Basic と Visual Studio IDE について少しはご理解いただけたかと思います。 さらに深く理解したい場合は、目次の**チュートリアル** セクションに示されているチュートリアルを続行してください。

## <a name="see-also"></a>関連項目

* [クイック スタート:Visual Studio で Visual Basic を使用してコンソール アプリを作成する](quickstart-visual-basic-console.md)
* [Visual Basic IntelliSense について](visual-basic-specific-intellisense.md)
