---
title: Visual Studio 2017 の概要
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a7667cac2a26a3e98d2e92dfeb13cee36d870e9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691161"
---
# <a name="visual-studio-ide-overview"></a>Visual Studio IDE の概要

Visual Studio 統合開発環境 (IDE) は、ほぼすべての種類のコードの表示や編集が可能で、アプリをデバッグ、ビルド、発行するために使用できるクリエイティブなランチパッドです。

Visual Studio は Windows と Mac で利用できます。 [Visual Studio for Mac](/visualstudio/mac/) は Visual Studio 2017 と同じ機能を多く備え、クロスプラットフォーム アプリとモバイル アプリの開発用に最適化されています。

この記事では、Windows 用の Visual Studio 2017 について説明します。 IDE の基本的な機能を紹介します。 簡単なプロジェクトの作成、コーディング支援としての IntelliSense の使用、プログラム実行中の変数の値を確認するためのアプリのデバッグなど、Visual Studio で実行できることをいくつか見ていきます。 さまざまなツール ウィンドウについても説明します。

## <a name="install-the-visual-studio-ide"></a>Visual Studio IDE のインストール

まず、[Visual Studio 2017 をダウンロード](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)してシステムにインストールします。

モジュラー インストーラーでは、*ワークロード* (好みのプログラミング言語やプラットフォームで必要な機能のグループ) を選択してインストールできます。 [プログラムの作成](#create-a-program)手順に従う場合は、インストール時に必ず、**[.NET Core クロスプラットフォームの開発]** ワークロードを選択します。 「[Visual Studio での C++ の概要](getting-started-with-cpp-in-visual-studio.md)」などのクイック スタートのトピックに、他のワークロードのインストールの説明があります。

![Visual Studio インストーラー](../ide/media/overview-net-core-workload.png)

Visual Studio を初めて起動する際には、Microsoft アカウント、仕事用アカウント、または学校用アカウントを使ってサインインすることもできます。

## <a name="tour-of-the-ide"></a>IDE のツアー

Visual Studio の全体像を視覚的に確認できるように、次のイメージには Visual Studio で開かれたプロジェクトと使用する可能性の高いいくつかの主なツール ウィンドウが示されています。

![Visual Studio IDE](../ide/media/visualstudioide.png)

- [ソリューション エクスプローラー](../ide/solutions-and-projects-in-visual-studio.md)では、コード ファイルを表示、移動、および管理できます。 ソリューション エクスプローラーでは、ファイルをソリューションやプロジェクトにまとめ、コードを整理できます。

- 大部分の時間を費やすことになる[エディター](../ide/writing-code-in-the-code-and-text-editor.md) ウィンドウではコードが表示され、ソース コードの編集や UI の設計を行うことができます。

- [[出力]](../ide/reference/output-window.md) ウィンドウには、デバッグ メッセージ、エラー メッセージ、コンパイラの警告、公開状態メッセージなど、Visual Studio の通知が出力されます。 メッセージ ソースごとに独自のタブがあります。

- [チーム エクスプローラー (VSTS)](/vsts/user-guide/work-team-explorer) では、[Git](https://git-scm.com/) や [Team Foundation バージョン管理 (TFVC)](/vsts/tfvc/overview) などのバージョン管理テクノロジを使用して、作業項目を追跡し、コードを他のユーザーと共有できます。

Visual Studio には他にも次のような一般的な生産性を高める機能が用意されています。

- [リファクタリング](../ide/refactoring-in-visual-studio.md)。これには、変数の名前をインテリジェントに変更する、選んだコード行を別個の関数に移動する、コードを他の場所に移動する、関数パラメーターを並べ替える、などの操作が含まれます。

   ![リファクタリング](../ide/media/VSIDE_refactor.png)

- [IntelliSense](../ide/using-intellisense.md) 。コードに関する型情報をエディターに直接表示したり、場合によっては、ちょっとしたコードを自動的に作成したりする、よく使われる機能セットの包括的な用語です。 エディター内のインラインに基本ドキュメントがあるようなもので、これによって、別個のヘルプ ウィンドウで型情報を検索する手間が省けます。 IntelliSense 機能は言語によって異なります。 詳細については、「[C# の IntelliSense](../ide/visual-csharp-intellisense.md)」、「[Visual C++ の IntelliSense](../ide/visual-cpp-intellisense.md)」、「[JavaScript IntelliSense](../ide/javascript-intellisense.md)」、および [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md) に関するページを参照してください。 次の図は、職場でのいくつかの IntelliSense 機能を示しています。

   ![Visual Studio のメンバーの一覧](../ide/media/vs2017_Intellisense.png)

- [クイック起動](../ide/reference/quick-launch-environment-options-dialog-box.md)検索ボックスは、Visual Studio で必要な情報を迅速に見つけるに役立ちます。 探している内容を表す名前を入力するだけで、Visual Studio に結果がリストされ、目的の場所に正確に移動できます。 また、**クイック起動**にはすべてのワークロードまたは個々のコンポーネントに対応する **Visual Studio インストーラー**を起動するリンクが表示されます。

   ![クイック起動検索ボックス](../ide/media/VSIDE_Tour_QuickLaunch.png)

- **波線**は波打った下線で、コード入力時にエラーや潜在的な問題をリアルタイムに警告します。 これにより、コンパイル時や実行時にエラーが検出されるのを待たずに即時に修正できます。 破線の上に移動すると、エラーに関する追加情報が表示されます。 電球とエラーを修正する方法が左余白に表示される場合もあります。 詳細については、[クイック アクション](../ide/quick-actions.md)に関するページを参照してください。

   ![波線](../ide/media/vs2017_squiggle.png)

- [[呼び出し階層]](../ide/reference/call-hierarchy.md) ウィンドウはテキスト エディターのコンテキスト メニューで開き、キャレット (挿入ポイント) の下のメソッドを呼び出す、またはそのメソッドによって呼び出されるメソッドを表示することができます。

   ![[呼び出し階層] ウィンドウ](../ide/media/VSIDE_call_hierarchy.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)。コードへの参照および変更、リンクされたバグ、作業項目、コード レビュー、単体テストをすべて、エディターを離れずに検索できます。

   ![CodeLens](../ide/media/codelensoverview.png)

- [ [ピークの定義](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) ] ウィンドウ。現在のコンテキストから移動せずに、メソッドまたは型の定義インラインが表示されます。

   ![ピークの定義](../ide/media/VSIDE_peek_definition.png)

- [ [定義に移動](../ide/go-to-and-peek-definition.md) ] コンテキスト メニュー オプション。関数またはオブジェクトが定義されている場所に直接移動します。 エディターを右クリックすることで、その他のナビゲーション コマンドも使用できます。

   ![定義へ移動](../ide/media/VSIDE_go_to_definition.png)

## <a name="create-a-program"></a>プログラムの作成

簡単なプログラムを新しく作成してみましょう。

1. Visual Studio を開きます。 メニューで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** を選択します。

  ![メニュー バーで [ファイル]、[新しいプロジェクト] の順に選択します。](../ide/media/VSIDE_Tour_NewProject1.png)

1. **[新しいプロジェクト]** ダイアログ ボックスには複数のプロジェクト "*テンプレート*" が表示されます。 テンプレートには、特定のプロジェクト タイプに必要な基本的なファイルと設定が含まれています。 **[Visual C#]** で **[.NET Core]** カテゴリを選択し、**[Console App (.NET Core)]\(コンソール アプリ (.NET Core)\)** テンプレートを選択します。 **[名前]** テキスト ボックスに「**HelloWorld**」と入力し、**[OK]** ボタンを選びます。

  ![.NET Core アプリ テンプレート](../ide/media/overview-new-project-dialog.png)

   Visual Studio によってプロジェクトが作成されます。 これは、リテラル文字列 "Hello World!" を表示する <xref:System.Console.WriteLine?displayProperty=nameWithType> メソッドを呼び出す単純な "Hello World" アプリケーションです。 コンソール ウィンドウに表示します。

  > [!NOTE]
  > **[.NET Core]** カテゴリが表示されない場合は、**[.NET Core クロスプラットフォームの開発]** ワークロードをインストールする必要があります。 これを実行するには、**[新しいプロジェクト]** ダイアログ ボックスの左下側の **[Visual Studio インストーラーを開く]** リンクをクリックします。 **Visual Studio インストーラー**が開いたら、**[.NET Core クロスプラットフォームの開発]** ワークロードまで下にスクロールして選択してから **[変更]** を選択します。

   すぐに次のようなグラフが表示されます。

   ![Visual Studio IDE](../ide/media/overview-ide-console-app.png)

   アプリケーションの C# コードは領域の大部分を占めるエディター ウィンドウに表示されます。 テキストは、キーワードや型など、コードの異なる要素を示すように自動的に色分けされます。 また、コードの縦の小さな点線は互いに一致する括弧を示し、行番号は後でコードの場所を探すのに役立ちます。 小さな四角で囲まれたマイナス記号を選択するとコードが折りたたまれ、折りたたまれている場合は展開できます。 このコードのアウトライン機能を使用すると、必要のないコードを非表示にして画面を整理できます。

   プロジェクト ファイルは右側の**ソリューション エクスプローラー**と呼ばれるウィンドウに一覧表示されます。

  ![赤色のボックスを持つ Visual Studio IDE](../ide/media/overview-ide-console-app-red-boxes.png)

  他にもメニューやツール ウィンドウが用意されていますが、今は次に進みましょう。

1. アプリを起動します。 そのためには、メニュー バーの **[デバッグ]** メニューから **[デバッグなしで開始]** を選択します。 あるいは、**Ctrl** + **F5 キー**を押します。

  ![[デバッグ]、[デバッグなしで開始] メニューを選択](../ide/media/overview-start-without-debugging.png)

  Visual Studio でアプリがビルドされ、コンソール ウィンドウが開き、メッセージ **Hello World!** が表示されます。 これで実行中のアプリができました。

  ![コンソール ウィンドウ](../ide/media/overview-console-window.png)

1. コンソール ウィンドウを閉じるには、キーボードで任意のキーを押します。

1. 何らかの追加コードをアプリに追加しましょう。 `Console.WriteLine("Hello World!");` という行の前に次の C# コードを追加します。

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   このコードはコンソール ウィンドウに **What is your name?** と表示し、ユーザーがテキストを入力して **Enter** キーを押すまで待機します。

1. `Console.WriteLine("Hello World!");` という行を次のコードに変更します。

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. **[デバッグ]** > **[デバッグなしで開始]** の順に選択するか、**Ctrl** + **F5** キーを押してアプリを再び実行します。

   Visual Studio によってアプリが再度ビルドされ、コンソール ウィンドウが開き、名前を入力するように求められます。

1. コンソール ウィンドウに名前を入力し、**Enter** キーを押します。

   ![コンソール ウィンドウの入力](media/overview-console-input.png)

1. 任意のキーを押してコンソール ウィンドウを閉じ、プログラムの実行を停止します。

## <a name="use-refactoring-and-intellisense"></a>リファクタリングと IntelliSense の使用

[リファクタリング](refactoring-in-visual-studio.md)と [IntelliSense](using-intellisense.md) がより効率的なコーディングに役立ついくつかの方法を見てみましょう。

最初に、変数 `name` の名前を変更します。

1. 変数 `name` をダブルクリックして選択します。

1. 変数の新しい名前として「`username`」と入力します。

   変数の周りに灰色のボックスが表示され、余白に電球が表示されることに注意してください。

1. 電球アイコンを選択して、使用可能な[クイック アクション](quick-actions.md)を表示します。 **['name' から 'username' へ名前を変更]** を選択します。

   ![Visual Studio での名前変更アクション](media/rename-quick-action.png)

   プロジェクト全体で変数の名前が変更され、この場合は 2 か所だけです。

   ![Visual Studio での名前変更リファクタリングを示すアニメーション gif](media/rename-refactoring.gif)

1. 次は IntelliSense を試してみましょう。 `Console.WriteLine($"\nHello {username}!");` という行の下に、「**DateTime now = DateTime.**」と入力します。

   ボックスに <xref:System.DateTime> クラスのメンバーが表示されます。 さらに、現在選択されているメンバーの説明が独立したボックスに表示されます。

   ![Visual Studio での IntelliSense リスト メンバー](media/intellisense-list-members.png)

1. **Now** という名前のメンバーを、ダブルクリックするか **Tab** キーを押して選択します。これはクラスのプロパティです。セミコロンを **;** 追加してコード行を完了します。

1. その下に、次のコード行を入力またはコピーします。

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> は <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> と少し異なり、出力の後に行終端記号を追加しません。 つまり、次に出力に送信されるテキストは、同じ書き出されます。 コードでこれらのメソッドをポイントすると、その説明が表示されます。

1. 次に、もう一度リファクタリングを使ってコードを少し簡単にします。 `DateTime now = DateTime.Now;` の行で変数 `now` をクリックします。

   その行の余白に小さいドライバー アイコンが表示されることに注意してください。

1. ドライバー アイコンをクリックして、Visual Studio で使用可能な推奨事項を確認します。 この場合は、全体の動作を変更することなくコードの行を削除する[インラインの一時変数](reference/inline-temporary-variable.md)リファクタリングが表示されています。

   ![Visual Studio でのインラインの一時変数リファクタリング](media/inline-temporary-variable-refactoring.png)

1. **[インラインの一時変数]** をクリックしてコードをリファクタリングします。

1. **Ctrl** + **F5** キーを押してプログラムを再び実行です。 出力は次のようになります。

   ![プログラムの出力が表示されたコンソール ウィンドウ](../ide/media/overview-console-final.png)

## <a name="debug-code"></a>コードのデバッグ

コードを記述するときは、実行してバグの存在を確認するために実際にテストする必要があります。 Visual Studio のデバッグ システムを使用すると、一度に 1 つのステートメントずつ、コードを実行して必要に応じて変数を検査できます。 指定した条件が True の場合にのみヒットするブレークポイントを設定することができます。 コードの実行中に変数の値などを監視できます。

ブレークポイントを設定して、プログラムが "実行中" の `username` 変数の値を見てみましょう。

1. `Console.WriteLine($"\nHello {username}!");` というコード行を探します。 この行にブレークポイントを設定するには、つまりこの行でプログラムの実行を一時停止するには、エディターの左端の余白をクリックします。 コード行の任意の場所をクリックしてから、**F9** キーを押してもかまいません。

   余白の左端に赤い円が表示され、コードが赤で強調表示されます。

   ![Visual Studio でのコード行のブレークポイント](media/breakpoint.png)

1. **[デバッグ]** > **[デバッグの開始]** を選択するか、**F5** キーを押して、デバッグを開始します。

1. コンソール ウィンドウが表示されて名前を要求されたら、入力して **Enter** キーを押します。

   Visual Studio コード エディターにフォーカスが戻り、ブレークポイントを設定したコード行が黄色で強調表示されます。 これは、プログラムが実行する次のコード行を示します。

1. `username` 変数をポイントすると、その値が表示されます。 または、`username` を右クリックして **[ウォッチを追加]** を選択し、変数を **[ウォッチ]** ウィンドウに追加して、そこで値を確認することもできます。

   ![Visual Studio でのデバッグ中の変数の値](media/debugging-variable-value.png)

1. プログラムを最後まで実行するには、**F5** キーを再び押します。

Visual Studio でのデバッグの詳細については、[デバッガーの機能ツアー](../debugger/debugger-feature-tour.md)に関するページをご覧ください。

## <a name="customize-visual-studio"></a>Visual Studio をカスタマイズする

既定の配色テーマの変更など、IDE をカスタマイズすることができます。 **濃色**テーマに変更するには:

1. メニュー バーから **[ツール]** > **[オプション]** の順に選択して、**[オプション]** ダイアログを開きます。

1. **[環境]**  >  **[全般]** オプションのページで、**[配色テーマ]** の選択内容を **[濃色]** に変更して **[OK]** を選択します。

   IDE 全体の配色テーマが**濃色**に変更されます。

   ![濃色テーマの VS](media/quickstart-personalize-dark-theme.png)

IDE の他のカスタマイズ方法については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」をご覧ください。

## <a name="learn-more"></a>詳細情報

Android または iOS のスマートフォン用のアプリを作成したいですか? 3D ゲームやクラウド対応のアプリはどうですか? これらをはじめとする Visual Studio の機能については、「[Features of Visual Studio 20171](../ide/advanced-feature-overview.md)」(Visual Studio 2017 の機能) をご覧ください。

コーディングをすぐに始められる場合は、目次から「[Visual Studio を使用して初めての ASP.NET Core Web アプリを作成する](quickstart-aspnet-core.md)」などのクイック スタート トピックを選んでください。

[Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033) で無料の Visual Studio コースを見ることもできます。

## <a name="see-also"></a>関連項目

* [Visual Studio のその他の機能](../ide/advanced-feature-overview.md)
* [www.visualstudio.com](https://www.visualstudio.com/vs/)
* [Visual Studio ブログ](https://blogs.msdn.microsoft.com/visualstudio/)
* [Visual Studio のダウンロード](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)