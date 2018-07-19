---
title: 'クイック スタート: Visual Studio で XAML と C# を使用して最初のユニバーサル Windows プラットフォーム アプリを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology:
- vs-acquisition
ms.topic: quickstart
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: dd638a539b8956716aa60b5361bd003c18d35f9b
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36283326"
---
# <a name="quickstart-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>クイック スタート: Visual Studio で XAML と C# を使用して最初のユニバーサル Windows プラットフォーム アプリを作成する

ここでは 5 分から 10 分で Visual Studio 統合開発環境 (IDE) の概要を示し、任意の Windows 10 デバイスで実行できる "Hello World" アプリケーションを作成します。 これの実行には、ユニバーサル Windows プラットフォーム (UWP) のプロジェクト テンプレート、Extensible Application Markup Language (XAML) および C# のプログラミング言語を使用します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、ユニバーサル Windows プラットフォーム プロジェクトを作成します。 この種類のプロジェクトには、必要となるすべてのテンプレート ファイルが付属していますので、何も追加する必要はありません。

1. Visual Studio 2017 を開きます。

2. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

3. **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで **[Visual C#]** を展開し、**[Windows ユニバーサル]** を選択します。 中央のペインで **[空のアプリ (ユニバーサル Windows)]** を選択します。 次いで、プロジェクトに「*HelloWorld*」という名前を付け、**[OK]** を選択します。

   ![Visual Studio IDE の [新しいプロジェクト] ダイアログ ボックスに示されている Windows ユニバーサル プロジェクト テンプレート](../ide/media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > **[空のアプリ (ユニバーサル Windows)]** プロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで **[Visual Studio インストーラーを開く]** リンクをクリックします。<br><br>![[新しいプロジェクト] ダイアログ ボックスで [Visual Studio インストーラーを開く] リンクをクリックする](../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Visual Studio インストーラーが起動します。 **[ユニバーサル Windows プラットフォーム開発]** ワークロードを選択し、**[変更]** を選択します。<br><br>![Visual Studio インストーラーの [ユニバーサル Windows プラットフォーム開発] ワークロード](../ide/media/uwp-dev-workload.png)

4. **[新しいユニバーサル Windows プラットフォーム プロジェクト]** ダイアログ ボックスが表示されたら、**[OK]** を選択します。

   ![[新しいユニバーサル Windows プラットフォーム プロジェクト] の既定のターゲット バージョンと最小バージョンの設定をそのまま使用します。](../ide/media/new-uwp-project-target-minver-dialog.png)

  > [!NOTE]
  > UWP アプリを作成するために Visual Studio を初めて使用する場合、**[設定]** ダイアログ ボックスが表示されます。 **[開発者モード]**、**[はい]** の順に選択します。<br><br>
 ![UWP 設定ダイアログ ボックスで開発者モードを有効にする](../ide/media/enable-developer-mode.png)<br><br>Visual Studio では、開発者モード パッケージが追加でインストールされます。 パッケージのインストールが完了したら、**[設定]** ダイアログ ボックスを閉じます。

## <a name="create-the-application"></a>アプリケーションを作成する

開発を始めるときがきました。 これから、ボタン コントロールを追加し、ボタンにアクションを追加し、"Hello World" アプリを起動してどのように動作するか確認します。

### <a name="add-a-button-to-the-design-canvas"></a>デザイン キャンバスにボタンを追加する

1. **ソリューション エクスプローラー**で、*MainPage.xaml* をダブルクリックして分割ビューを開きます。

  ![ソリューション エクスプローラーで MainPage.xaml を開く ](../ide/media/uwp-solution-explorer-MainPage-xaml.png)

  デザイン キャンバスを含む **XAML デザイナー**と、コードを追加または変更できる **XAML エディター**の 2 つのウィンドウがあります。

  ![XAML エディターの XAML デザイナー ウィンドウ](../ide/media/uwp-xaml-editor.png)

2. **[ツールボックス]** を選択して、ツールボックスのスライド アウト ウィンドウを開きます。

  ![[ツールボックス] をクリックしてツールボックスのスライド アウト ウィンドウを開く](../ide/media/uwp-toolbox.png)

  (**ツールボックス**のオプションが表示されない場合は、メニュー バーから開くことができます。 これを行うには、**[ビュー]** > **[ツールバー]** の順に選択します。 または、**Ctrl**+**Alt**+**X** キーを押します)。

3. **[ピン設定]** アイコンをクリックして、[ツールボックス] ウィンドウをドッキングします。

  ![[ピン設定] アイコンをクリックして [ツールボックス] ウィンドウをドッキングする](../ide/media/uwp-toolbox-autohide.png)

4. **[ボタン]** コントロールをクリックし、デザイン キャンバスまでドラッグします。

   ![[ボタン] コントロールをクリックしデザイン キャンバスまでドラッグする](../ide/media/uwp-toolbox-add-button-control.png)

  **XAML エディター**でコードを参照すると、そこにもボタンが追加されていることを確認できます。

  ![[ボタン] コントロールをクリックしデザイン キャンバスまでドラッグする](../ide/media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>ボタンにラベルを追加する

1. **XAML エディター**で、ボタンのコンテンツ値を "Button" から "Hello World!" に変更します。

   ![ボタンのコンテンツ値を Hello World に変更する](../ide/media/uwp-change-button-text-in-xaml-code-window.png)

2. **XAML デザイナー**のボタンも変更されることに注目してください。

   ![デザイン キャンバスでボタンが Hello World に変更する](../ide/media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>イベント ハンドラーを追加する

「イベント ハンドラー」とは、難しそうに聞こえますが、イベントが発生したときに呼び出されるコードの単なる別名です。 この場合、"Hello World!" ボタンにアクション を追加します。

1. デザイン キャンパスでボタン コントロールをダブルクリックします。

2. 分離コード ページの *MainPage.xaml.cs* でイベント ハンドラー コードを編集します。

 ポイントはここからです。 既定のイベント ハンドラーは次のようになります。

   ![既定の Button_Click イベント ハンドラー ](../ide/media/uwp-button-click-code.png)

 これを次のように変更してみます。

    ![新しい非同期の Button_Click イベント ハンドラー ](../ide/media/uwp-add-hello-world-async-code.png)

  コピーして貼り付けるコードは次のとおりです。

  ```C#
  private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
  ```

#### <a name="what-did-we-just-do"></a>行った処理

コードでいくつかの Windows API が使用され、いくつかのテキストを読み上げられる、音声合成オブジェクトが作成されました。 (`SpeechSynthesis` の使用に関する詳細は、「<xref:System.Speech.Synthesis>」をご覧ください)。

## <a name="run-the-application"></a>アプリケーションの実行

"Hello World" UWP アプリを、ビルド、配置、および起動して、どのように表示および読み上げがあるか確認してみましょう。 ここではその方法を説明します。

1. **[ローカル マシン]** を選択してアプリケーションを起動します。

   ![[ローカル マシン] をクリックし、UWP アプリを起動してデバッグする](../ide/media/uwp-start-or-debug.png)

   (または、メニュー バーから **[デバッグ]** > **[デバッグの開始]** を選択するか、**F5** キーを押してアプリを開始します)。

2. スプラッシュ スクリーンが消えるとすぐ表示されるアプリを確認します。 アプリは次のように表示されるはずです。

   ![UWP "Hello World" アプリ](../ide/media/uwp-hello-world-app.png)

3. **[Hello World]** ボタンをクリックします。

 Windows 10 デバイスにより、"Hello, World!" と文字通り読み上げられます。

4. アプリを閉じるには、ツール バーで **[デバッグの停止]** ボタンをクリックします。 (または、メニュー バーから **[デバッグ]**+**[デバッグの停止]** を選択するか、**Shift** > **F5** キーを押します)。

## <a name="next-steps"></a>次の手順

このクイック スタートは完了しました。 これで UWP および Visual Studio IDE の基本を学習できたはずです。 詳細については、引き続き以下のチュートリアルをご覧ください。

> [!div class="nextstepaction"]
> [ユーザー インターフェイスを作成する](/windows/uwp/design/basics/xaml-basics-ui)
