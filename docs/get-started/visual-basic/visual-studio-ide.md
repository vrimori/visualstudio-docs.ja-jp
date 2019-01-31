---
title: Visual Basic 開発者向けの概要
ms.date: 11/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 113a333c7a1ca100b6572f730ec9291ffc20ff87
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939180"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Visual Studio IDE へようこそ | Visual Basic

Visual Studio *統合開発環境* は、コードの編集、デバッグ、ビルドを行ってから、アプリを発行するために使用できるクリエイティブなランチパッドです。 統合開発環境 (IDE) は、ソフトウェア開発の多くの側面で使用できる機能を豊富に備えたプログラムです。 大部分の IDE が備える標準的なエディターおよびデバッガーに加えて、Visual Studio ではコンパイラ、コード補完ツール、グラフィック デザイナーなど、ソフトウェア開発プロセスを容易にする多くの機能を用意しています。

![Visual Studio IDE](../media/visual-studio-ide.png)

これはプロジェクトを開いている Visual Studio の画像です。使用頻度が高いツール ウィンドウがいくつか開いています。

- [**ソリューション エクスプローラー**](../../ide/solutions-and-projects-in-visual-studio.md) (右上) では、コード ファイルを表示、移動、および管理できます。 **ソリューション エクスプローラー**では、ファイルを[ソリューションやプロジェクト](tutorial-projects-solutions.md)にまとめ、コードを整理できます。

- 大部分の時間を費やすことになる[エディター ウィンドウ](../../ide/writing-code-in-the-code-and-text-editor.md) (中央) にはファイルの内容が表示されます。 ここでは、コードを編集したり、ボタンやテキスト ボックスを持つウィンドウなどのユーザー インターフェイスをデザインすることができます。

- [[出力]](../../ide/reference/output-window.md) ウィンドウ (下中央) には、デバッグ メッセージ、エラー メッセージ、コンパイラの警告、公開状態メッセージなど、Visual Studio の通知が出力されます。 メッセージ ソースごとに独自のタブがあります。

- [チーム エクスプローラー](/azure/devops/user-guide/work-team-explorer?view=vsts) (右下) では、[Git](https://git-scm.com/) や [Team Foundation バージョン管理 (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) などのバージョン管理テクノロジを使用して、作業項目を追跡し、コードを他のユーザーと共有できます。

## <a name="editions"></a>エディション

Visual Studio は Windows と Mac で利用できます。 [Visual Studio for Mac](/visualstudio/mac/) は Visual Studio 2017 と同じ機能を多く備え、クロスプラットフォーム アプリとモバイル アプリの開発用に最適化されています。 この記事では、Windows バージョンの Visual Studio 2017 について説明します。

Community、Professional、Enterprise という 3 つのエディションの Visual Studio 2017 があります。 各エディションでサポートされている機能については、「[Visual Studio 2017 IDE の比較](https://visualstudio.microsoft.com/vs/compare/)」を参照してください。

## <a name="popular-productivity-features"></a>よく使われる生産性機能

ソフトウェアを開発する際に、生産性を高めるために Visual Studio でよく使われる機能のいくつかを以下に示します。

- [リファクタリング](../../ide/refactoring-in-visual-studio.md)

   リファクタリングには、変数の名前をインテリジェントに変更する、1 つまたは複数のコード行を新しいメソッドに抽出する、メソッド パラメーターを並べ替える、などの操作が含まれます。

   ![Visual Studio でのリファクタリング](media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense は、コードに関する情報をエディターに直接表示したり、場合によっては、ちょっとしたコードを自動的に作成したりする機能のセットを表す用語です。 エディター内のインラインに基本ドキュメントがあるようなもので、これによって、他の場所で型情報を検索する手間が省けます。 IntelliSense 機能は言語によって異なります。 詳細については、「[C# の IntelliSense](../../ide/visual-csharp-intellisense.md)」、「[Visual C++ の IntelliSense](../../ide/visual-cpp-intellisense.md)」、「[JavaScript IntelliSense](../../ide/javascript-intellisense.md)」、および [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md) に関するページを参照してください。 次の図は、IntelliSense によって型のメンバー リストがどのように表示されるかを示したものです。

   ![Visual Studio のメンバーの一覧](media/intellisense-list-members.png)

- [クイック起動](../../ide/reference/quick-launch-environment-options-dialog-box.md)

   Visual Studio には非常に多くのメニュー、オプション、およびプロパティがあるため、手に負えないもののように思える場合があるかもしれません。 **クイック起動**検索ボックスは、Visual Studio で必要な情報を迅速に見つけるに役立ちます。 探しているものを表す名前の入力を開始すると、Visual Studio に結果がリストされ、目的の場所に正確に移動できます。 Visual Studio に機能を追加する必要がある場合 (追加のプログラミング言語に対するサポートを追加するなど)、**クイック起動**の結果としてワークロードまたは個々のコンポーネントをインストールする Visual Studio インストーラーが開かれます。

   ![Visual Studio でのクイック起動検索ボックス](../media/quick-launch-nuget.png)

- 波線と[クイック アクション](../../ide/quick-actions.md)

   波線は波打った下線で、コード入力時にエラーや潜在的な問題を警告します。 このような視覚的な手がかりを利用することにより、ビルド中またはプロフラム実行時にエラーが検出されるのを待たなくても問題をすぐに修正することができます。 波線の上に移動すると、エラーに関する追加情報が表示されます。 電球とエラーを修正する方法 (クイック アクションとして知られている) が左余白に表示される場合もあります。

   ![Visual Studio での波線](media/squiggles-error.png)

- [呼び出し階層](../../ide/reference/call-hierarchy.md)

   **[呼び出し階層]** ウィンドウには、選択したメソッドを呼び出すメソッドが表示されます。 この情報は、メソッドの変更や削除について考えるとき、またはバグの追跡を試みるときに有用です。

   ![Visual Studio での [呼び出し階層] ウィンドウ](media/call-hierarchy.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens を使用すると、コードへの参照、コードへの変更、リンクされたバグ、作業項目、コード レビュー、単体テストをすべて、エディターから離れずに楽に検索できます。

   ![Visual Studio の CodeLens](media/codelens.png)

   > [!NOTE]
   > CodeLens は Visual Studio 2017 Community エディションでは使用できません。

- [定義に移動](../../ide/go-to-and-peek-definition.md)

   [定義に移動] 機能では、関数または型が定義されている場所に直接移動できます。

   ![Visual Studio の [定義に移動]](media/go-to-definition-menu.png)

- [定義をここに表示](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   **[ピークの定義]** ウィンドウには、実際に個々のファイルを開かなくても、メソッドまたは型の定義が表示されます。

   ![Visual Studio の [定義のピーク]](media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Visual Studio IDE のインストール

この概要記事では、簡単なプロジェクトを作成し、Visual Studio の機能をいくつか試します。Visual Studio では、配色テーマを変更したり、コーディング補助として [IntelliSense](../../ide/using-intellisense.md) を使用したり、アプリをデバッグしてプログラム実行中の変数の値を参照したりできます。 まず、[Visual Studio 2017 をダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)してシステムにインストールします。

モジュラー インストーラーでは、*ワークロード* (好みのプログラミング言語やプラットフォームで必要な機能のグループ) を選択してインストールできます。 [プログラムの作成](#create-a-program)手順に従う場合は、インストール時に必ず、**[.NET Core クロスプラットフォームの開発]** ワークロードを選択します。

![Visual Studio インストーラーの [.NET Core クロスプラットフォームの開発] ワークロード](../media/dotnet-core-cross-platform-workload.png)

Visual Studio を初めて起動する際には、Microsoft アカウント、仕事用アカウント、または学校用アカウントを使って[サインイン](../../ide/signing-in-to-visual-studio.md)することもできます。

## <a name="customize-visual-studio"></a>Visual Studio をカスタマイズする

既定の配色テーマの変更など、Visual Studio ユーザー インターフェイスをカスタマイズできます。

### <a name="change-the-color-theme"></a>[配色テーマ] を変更する

**濃色**テーマに変更するには:

1. メニュー バーから **[ツール]** > **[オプション]** の順に選択して、**[オプション]** ダイアログを開きます。

2. **[環境]**  >  **[全般]** オプションのページで、**[配色テーマ]** の選択内容を **[濃色]** に変更して **[OK]** を選択します。

   ![Visual Studio で配色テーマを濃色に変更する](media/change-color-theme.png)

   IDE 全体の配色テーマが**濃色**に変更されます。

   ![ダーク テーマでの Visual Studio](../../ide/media/quickstart-personalize-dark-theme.png)

### <a name="select-environment-settings"></a>環境設定を選択する

次に、Visual Basic 開発者に合わせた環境設定を使用するように Visual Studio を構成します。

1. メニュー バーで、**[ツール]** > **[設定のインポートとエクスポート]** の順にクリックします。

2. **設定のインポートとエクスポート ウィザード**の最初のページで **[すべての設定をリセット]** を選択し、**[次へ]** を選択します。

3. **[現在の設定の保存]** ページで、現在の設定を保存するオプションを選択するか選択せずに、**[次へ]** を選択します  (設定をカスタマイズしていない場合は、**[No, just reset settings, overwriting my current settings]\(いいえ、設定をリセットして現在の設定を上書きするだけです\)** を選択します)。

4. **[設定の既定のコレクションの選択]** ページで、**[Visual Basic]** を選択し、**[完了]** を選択します。

5. **[リセットの完了]** ページで **[閉じる]** を選択します。

IDE の他のカスタマイズ方法については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」をご覧ください。

## <a name="create-a-program"></a>プログラムの作成

簡単なプログラムを作成してみましょう。

1. Visual Studio を開きます。 メニュー バーで **[ファイル]** > **[新規プロジェクト]** を選択します。

   ![メニュー バーで [ファイル]、[新しいプロジェクト] の順に選択します。](media/file-new-project-menu.png)

2. **[新しいプロジェクト]** ダイアログ ボックスには複数のプロジェクト "*テンプレート*" が表示されます。 テンプレートには、特定のプロジェクト タイプに必要な基本的なファイルと設定が含まれています。 **[Visual Basic]** で **[.NET Core]** カテゴリを選択し、**[Console App (.NET Core)]\(コンソール アプリ (.NET Core)\)** テンプレートを選択します。 **[名前]** テキスト ボックスに「**HelloWorld**」と入力し、**[OK]** ボタンを選びます。

   ![.NET Core アプリ テンプレート](media/overview-npd.png)

   > [!NOTE]
   > **[.NET Core]** カテゴリが表示されない場合は、**[.NET Core クロスプラットフォームの開発]** ワークロードをインストールする必要があります。 これを実行するには、**[新しいプロジェクト]** ダイアログ ボックスの左下側の **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが開いたら、**[.NET Core クロスプラットフォームの開発]** ワークロードまで下にスクロールして選択してから **[変更]** を選択します。

   Visual Studio によってプロジェクトが作成されます。 これは、リテラル文字列 "Hello World!" を表示する <xref:System.Console.WriteLine?displayProperty=nameWithType> メソッドを呼び出す単純な "Hello World" アプリケーションです。 コンソール (プログラムの出力) ウィンドウでに表示されます。

   すぐに次のようなグラフが表示されます。

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   アプリの Visual Basic コードは、領域の大部分を占めるエディター ウィンドウに表示されます。 キーワードや型など、コードの異なる部分を示すようにテキストが自動的に色分けされているのに注目してください。 また、コードの縦の小さな点線は互いに一致する括弧を示し、行番号は後でコードの場所を探すのに役立ちます。 小さな四角で囲まれたマイナス記号を選択するとコード ブロックが折りたたまれ、折りたたまれている場合は展開できます。 このコードのアウトライン機能を使用すると、必要のないコードを非表示にして画面を整理できます。 プロジェクト ファイルは右側の**ソリューション エクスプローラー**と呼ばれるウィンドウに一覧表示されます。

   ![赤色のボックスを持つ Visual Studio IDE](media/overview-ide-console-app-red-boxes.png)

   他にもメニューやツール ウィンドウが用意されていますが、今は次に進みましょう。

3. ここで、**Ctrl**+**F5** キーを押してアプリを起動します。

   Visual Studio でアプリがビルドされ、コンソール ウィンドウが開き、メッセージ **Hello World!** が表示されます。 これで実行中のアプリができました。

   ![コンソール ウィンドウ](../media/overview-console-window.png)

4. コンソール ウィンドウを閉じるには、キーボードで任意のキーを押します。

5. 何らかの追加コードをアプリに追加しましょう。 `Console.WriteLine("Hello World!")` という行の前に次の Visual Basic コードを追加します。

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   このコードはコンソール ウィンドウに **What is your name?** と表示し、ユーザーがテキストを入力して **Enter** キーを押すまで待機します。

6. `Console.WriteLine("Hello World!")` という行を次のコードに変更します。

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

7. **Ctrl**+**F5** キーを押してプログラムを再び実行します。

   Visual Studio によってアプリが再度ビルドされ、コンソール ウィンドウが開き、名前を入力するように求められます。

8. コンソール ウィンドウに名前を入力し、**Enter** キーを押します。

   プログラムは名前を使用してあいさつします。

   ![コンソール ウィンドウの入力](media/overview-console-input.png)

9. 任意のキーを押してコンソール ウィンドウを閉じ、プログラムの実行を停止します。

## <a name="use-refactoring-and-intellisense"></a>リファクタリングと IntelliSense の使用

[リファクタリング](../../ide/refactoring-in-visual-studio.md)と [IntelliSense](../../ide/using-intellisense.md) がより効率的なコーディングに役立ついくつかの方法を見てみましょう。

最初に、変数 `name` の名前を変更します。

1. 変数 `name` をダブルクリックして選択します。

2. 変数の新しい名前として「**username**」と入力します。

   変数の周りに灰色のボックスが表示され、余白に電球が表示されることに注意してください。

3. 電球アイコンを選択して、使用可能な[クイック アクション](../../ide/quick-actions.md)を表示します。 **['name' から 'username' へ名前を変更]** を選択します。

   ![Visual Studio での名前変更アクション](media/rename-quick-action.png)

   プロジェクト全体で変数の名前が変更され、この場合は 2 か所だけです。

4. 次は IntelliSense を試してみましょう。 `Console.WriteLine("Hello " + username + "!")` という行の下に、次のコード フラグメントを入力します。

    ```vb
   Dim now = Date.
   ```

   ボックスに <xref:System.DateTime> クラスのメンバーが表示されます。 さらに、現在選択されているメンバーの説明が独立したボックスに表示されます。

   ![Visual Studio での IntelliSense リスト メンバー](media/intellisense-list-members.png)

5. クラスのプロパティである **Now** という名前のメンバーを選択します。それをダブルクリックするか、上下の矢印キーを使用して選択した後 **Tab** キーを押します。

6. その下に、次のコード行を入力するか貼り付けます。

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> は <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> と少し異なり、出力の後に行終端記号を追加しません。 つまり、次に出力に送信されるテキストは、同じ書き出されます。 コードでこれらのメソッドをポイントすると、その説明が表示されます。

7. 次に、もう一度リファクタリングを使ってコードを少し簡単にします。 `Dim now = Date.Now` の行で変数 `now` をクリックします。

   その行の余白に小さいドライバー アイコンが表示されることに注意してください。

8. ドライバー アイコンをクリックして、Visual Studio で使用可能な推奨事項を確認します。 この場合は、コードの全体の動作を変更することなくコードの行を削除する[インラインの一時変数](../../ide/reference/inline-temporary-variable.md)リファクタリングが表示されています。

   ![Visual Studio でのインラインの一時変数リファクタリング](media/inline-temporary-variable-refactoring.png)

9. **[インラインの一時変数]** をクリックしてコードをリファクタリングします。

10. **Ctrl** + **F5** キーを押してプログラムを再び実行です。 出力は次のようになります。

    ![プログラムの出力が表示されたコンソール ウィンドウ](media/overview-console-final.png)

## <a name="debug-code"></a>コードのデバッグ

コードを記述するときは、実行してバグの存在を確認するために実際にテストする必要があります。 Visual Studio のデバッグ システムを使用すると、一度に 1 つのステートメントずつ、コードを実行して必要に応じて変数を検査できます。 特定の行でコードの実行を停止する "*ブレークポイント*" を設定できます。 コードが実行されたときに変数の値がどのように変わるかなどを確認できます。

ブレークポイントを設定して、プログラムが "実行中" の `username` 変数の値を見てみましょう。

1. `Console.WriteLine("Hello " + username + "!")` というコード行を探します。 この行にブレークポイントを設定するには、つまりこの行でプログラムの実行を一時停止するには、エディターの左端の余白をクリックします。 コード行の任意の場所をクリックしてから、**F9** キーを押してもかまいません。

   余白の左端に赤い円が表示され、コードが赤で強調表示されます。

   ![Visual Studio でのコード行のブレークポイント](media/breakpoint.png)

1. **[デバッグ]** > **[デバッグの開始]** を選択するか、**F5** キーを押して、デバッグを開始します。

1. コンソール ウィンドウが表示されて名前を要求されたら、入力して **Enter** キーを押します。

   Visual Studio コード エディターにフォーカスが戻り、ブレークポイントを設定したコード行が黄色で強調表示されます。 これは、プログラムが実行する次のコード行を示します。

1. `username` 変数をポイントすると、その値が表示されます。 または、`username` を右クリックして **[ウォッチを追加]** を選択し、変数を **[ウォッチ]** ウィンドウに追加して、そこで値を確認することもできます。

   ![Visual Studio でのデバッグ中の変数の値](media/debugging-variable-value.png)

1. プログラムを最後まで実行するには、**F5** キーを再び押します。

Visual Studio でのデバッグの詳細については、[デバッガーの機能ツアー](../../debugger/debugger-feature-tour.md)に関するページをご覧ください。

## <a name="next-steps"></a>次の手順

以下の入力記事のいずれかに従って、Visual Studio をさらに詳しく調べます。

> [!div class="nextstepaction"]
> [コード エディターの使用方法について学習する](tutorial-editor.md)

> [!div class="nextstepaction"]
> [プロジェクトとソリューションについて学習する](tutorial-projects-solutions.md)

## <a name="see-also"></a>関連項目

- [Visual Studio のその他の機能](../../ide/advanced-feature-overview.md)を確認します
- [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/) にアクセスします
- [Visual Studio ブログ](https://blogs.msdn.microsoft.com/visualstudio/)を参照します
- [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033) で無料の Visual Studio コースを確認します