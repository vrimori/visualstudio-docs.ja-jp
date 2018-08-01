---
title: Visual Studio IDE のツアー
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89689df19e5002c4c757d5a84c9263f8c40a10e7
ms.sourcegitcommit: b544e2157ac20866baf158eef9cfed3e3f1d68b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2018
ms.locfileid: "39388190"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>クイックスタート: Visual Studio IDE の表示の紹介

この 5 - 10 分程度の Visual Studio 統合開発環境 (IDE) の紹介では、ウィンドウやメニューなどの UI 機能の一部を説明します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="start-page"></a>スタート ページ

ほとんどの場合、Visual Studio を起動するとまず**スタート ページ**が表示されます。 **スタート ページ**は、必要なコマンドとプロジェクト ファイルを見つけやすくする "ハブ" として設計されています。 **[最近]** セクションには、プロジェクトと最近作業したフォルダーが表示されます。 **[新しいプロジェクト]** の下にあるリンクをクリックすると、**[新しいプロジェクト]** ダイアログ ボックスが開きます。また、**[開く]** では、既存のコード プロジェクトやフォルダーを開くことができます。 右側には、最新の開発者向けニュース フィードが表示されます。

![Visual Studio の [スタート ページ]](media/start-page.png)

**スタート ページ**を閉じた後でもう一度表示する場合は、**[ファイル]** メニューで再度開くことができます。

![Visual Studio の [ファイル] メニュー](media/quickstart-IDE-file-menu-large.png)

## <a name="create-a-project"></a>プロジェクトを作成する

Visual Studio の機能を引き続き確認するために、新しいプロジェクトを作成しましょう。

1. **[スタート ページ]** の **[新しいプロジェクト]** の下にある検索ボックスに「**console**」と入力し、プロジェクトの種類の一覧をフィルターして、名前に "console" が含まれるものに絞り込みます。

   ![Visual Studio の [スタート ページ] でプロジェクト テンプレートを検索する](media/start-page-search-templates.png)

   Visual Studio には、すぐにコーディングを開始するのに役立つ、さまざまな種類のプロジェクト テンプレートが用意されています。 C# の **[コンソール アプリ (.NET Framework)**] プロジェクト テンプレートを選択します  (Visual Basic、C++、Javascript など他の言語で開発している場合は、それらの言語のいずれかでプロジェクトを作成してもかまいません。 表示される UI はすべてのプログラミング言語でほぼ同じです)。

1. 表示された **[新しいプロジェクト]** ダイアログ ボックスで、既定のプロジェクト名をそのまま使用し、**[OK]** を選択します。

   プロジェクトが作成され、*Program.cs* という名前のファイルが **[エディター]** ウィンドウに開きます。 **エディター**にファイルの内容が表示されます。Visual Studio でのコード作成作業のほとんどは、このエディターで行います。

   ![Visual Studio のエディター](media/editor.png)

## <a name="solution-explorer"></a>ソリューション エクスプローラー

通常は Visual Studio の右側にある**ソリューション エクスプローラー**には、プロジェクト、ソリューション、コード フォルダー内のファイルとフォルダーの階層がグラフィカルに表示されます。 **ソリューション エクスプローラー**内で階層を移動し、ファイルを選択できます。

![Visual Studio のソリューション エクスプローラー](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>メニュー

Visual Studio の上部にあるメニュー バーには、コマンドがカテゴリごとにグループ化されています。 たとえば、**[プロジェクト]** メニューには、作業中のプロジェクトに関連するコマンドが含まれています。 **[ツール]** メニューでは、**[オプション]** を選択して Visual Studio の動作をカスタマイズしたり、**[ツールと機能を取得]** を選択してインストールに機能を追加したりできます。

![Visual Studio のメニュー バー](media/quickstart-IDE-menu-bar.png)

**[表示]** メニューの **[エラー一覧]** を選択して、**[エラー一覧]** ウィンドウを開いてみましょう。

## <a name="error-list"></a>エラー一覧

**[エラー一覧]** ウィンドウには、現在の状態のコードに関するエラー、警告、メッセージが表示されます。 ファイル、またはプロジェクト内のどこかにエラー (中かっこやセミコロンの欠落など) がある場合は、ここに一覧表示されます。

![Visual Studio の [エラー一覧]](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>[出力] ウィンドウ

**[出力]** ウィンドウには、プロジェクトのビルド時の出力メッセージや、ソース管理プロバイダーからの出力メッセージが表示されます。

プロジェクトをビルドして、ビルド出力をいくつか確認してみましょう。 **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。 自動的に **[出力]** ウィンドウにフォーカスされ、ビルドが成功したことを示すメッセージが表示されます。

![Visual Studio の [出力] ウィンドウ](media/build-output-minimal.png)

## <a name="quick-launch"></a>クイック起動

**[クイック起動]** ボックスでは、Visual Studio でのほぼすべての操作をすばやく簡単に行うことができます。 実行する操作に関連したテキストを入力すると、そのテキストに関係するオプションの一覧が表示されます。 たとえば、ビルドで実際に行われる内容をさらに詳しく表示するために、ビルド出力の詳細レベルを上げるとします。 これは次のように行います。

1. **[クイック起動]** ボックスに「**verbosity**」と入力します。 **[オプション]** カテゴリで、表示された結果から **[プロジェクトおよびソリューション] --> [ビルド/実行]** を選択します。

   ![Visual Studio の [クイック起動] ボックス](media/quickstart-IDE-quick-launch.png)

   **[オプション]** ダイアログ ボックスが開き、**[ビルド/実行]** オプションのページが表示されます。

1. **[MSBuild プロジェクト ビルドの出力の詳細]** で **[標準]** を選択し、**[OK]** をクリックします。

1. **ソリューション エクスプローラー**で **[ConsoleApp1]** プロジェクトを右クリックし、コンテキスト メニューで **[リビルド]** を選択して、プロジェクトをもう一度ビルドします。

   今度は、**[出力]** ウィンドウには、どの場所のどのファイルがコピーされたかなど、ビルド プロセスに関するより詳細なログが表示されます。

   ![Visual Studio の詳細なビルド出力](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>[フィードバックの送信] メニュー

Visual Studio の使用中に問題が発生した場合、または製品の改善案をお持ちの場合は、Visual Studio ウィンドウ上部の **[クイック起動]** ボックスの横にある、**[フィードバックの送信]** メニューを使用してください。

![Visual Studio の [フィードバックの送信] メニュー](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>次の手順

ユーザー インターフェイスに慣れるため、Visual Studio の機能をいくつか確認しました。 下記に従って、さらに試してみてください。

- 「[Visual Studio IDE の概要](../ide/visual-studio-ide.md)」で、Visual Studio のより詳細なツアーに参加し、デバッグも試してみてください。

- [[エラー一覧]](../ide/reference/error-list-window.md)、[[出力] ウィンドウ](../ide/reference/output-window.md)、[[プロパティ] ウィンドウ](../ide/reference/properties-window.md)、[[オプション] ダイアログ ボックス](../ide/reference/options-dialog-box-visual-studio.md)など、ウィンドウの詳細について説明した VS ドキュメントの**一般的なユーザー インターフェイス要素**に関するセクションをご覧ください。

## <a name="see-also"></a>関連項目

- [クイックスタート: IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)
- [クイック スタート: エディターでのコードの作成](../ide/quickstart-editor.md)
- [クイック スタート: プロジェクトとソリューション](../ide/quickstart-projects-solutions.md)