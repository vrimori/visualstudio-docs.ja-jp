---
title: "R Tools for Visual Studio の使用を開始する | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39228cf0-8d21-43bb-a2ce-5e5fdc81ec41
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 27c16d7315acaa0efd4aa8b866b44784ffe056a4
ms.contentlocale: ja-jp
ms.lasthandoff: 05/12/2017

---

# <a name="getting-started-with-r-tools-for-visual-studio"></a>R Tools for Visual Studio の使用を開始する

R Tools for Visual Studio (RTVS) をインストールすると ([インストール](installation.md)に関するページを参照してください)、ツールが提供するエクスペリエンスをすばやく確認できます。 次のセクションでは、簡単なツアーを紹介します。

- [R プロジェクトの作成](#create-an-r-project)
- [対話型ウィドウと IntelliSense の調査](#explore-the-interactive-window-and-intellisense)
- [コード編集機能の体験](#experience-code-editing-features)
- [コードのデバッグ](#debugging-your-code)
- [次のステップ](#next-steps)

## <a name="create-an-r-project"></a>R プロジェクトの作成

1. Visual Studio を起動します。
1. **[ファイル]、[新規]、[プロジェクト]** の順に選択します。(Ctrl+Shift+N)
1. **[テンプレート]、[R]** で "R Project" を選択し、プロジェクトに名前と場所を指定し、**[OK]** を選択します。

   ![Visual Studio 内の R (VS2017 の RTVS) の [新しいプロジェクト] ダイアログ ボックス](~/rtvs/media/getting-started-01-new-project.png)

1. プロジェクトを作成すると、次の内容が表示されます。

    - 右側には、Visual Studio ソリューション エクスプローラーがあり、ここには含まれる*ソリューション*内にプロジェクトが表示されます。 (ソリューションには、複数のさまざまな種類のプロジェクトを含めることができます。詳細については、[プロジェクト](projects.md)に関するページを参照してください。)
    - 左上には、新しい R ファイル (`script.R`) があり、ここでは、すべての Visual Studio の編集機能を使ってソース コードを編集することができます。
    - 左下には、**[R インタラクティブ]** ウィンドウがあり、ここでは対話型でコードを開発およびテストすることができます。

> [!Note]
> プロジェクトを開かずに、別のプロジェクトの種類を読み込む場合にも、**[R インタラクティブ]** ウィンドウを使用できます。 いつでも **[R Tools] > [Windows] > [R インタラクティブ]** を選択するだけです。

## <a name="explore-the-interactive-window-and-intellisense"></a>対話型ウィドウと IntelliSense の調査

1. 「`3 + 4`」と入力して Enter キーを押し、結果を表示して、対話型ウィンドウが動作していることをテストします。

    ![Visual Studio 2017 (VS2017) の R 対話型ウィンドウ](~/rtvs/media/getting-started-02-interactive1.png)

1. 少し複雑な「`ds <- c(1.5, 6.7, 8.9) * 1:12`」を入力してから、「`ds`」を入力して結果を表示します。

    ![その他の Visual Studio の R 対話型の例](~/rtvs/media/getting-started-03-interactive2.png)

1. 「`mean(ds)`」を入力しますが、「`m`」や「`me`」と入力すると、すぐに Visual Studio IntelliSense で次のようにオート コンプリート オプションが提供されることに気付きます。 リストから目的のオート コンプリートを選択したら、Tab キーを押して挿入します。方向キーやマウスで選択を変更することができます。

    ![コードの入力時に表示される IntelliSense](~/rtvs/media/getting-started-04-intellisense1.png)

1. `mean` が完成したら、先頭のかっこ「`(`」を入力すると、IntelliSense で関数に対するインライン ヘルプが示されることを確認できます。

    ![IntelliSense が示す関数のヘルプ](~/rtvs/media/getting-started-05-intellisense2.png)

1. 行 `mean(ds)` を完成させ、Enter キーを押すと、結果が表示されます (`[1] 39.51667`)。

1. 対話型ウィンドウは、ヘルプと統合されているため、たとえば、「`?mean`」と入力すると、Visual Studio の **[R ヘルプ]** ウィンドウにその関数のヘルプが表示されます。 この機能の詳細については、「[R Tools for Visual Studio のヘルプ](getting-started-help.md)」を参照してください。

    ![Visual Studio の [R ヘルプ] ウィンドウ](~/rtvs/media/getting-started-06-help.png)

1. 一部のコマンド (`plot(1:100)` など) では、出力が対話型ウィンドウに直接表示できない場合、Visual Studio 内に新しいウィンドウが開かれます。

    ![Visual Studio でのプロットの表示](~/rtvs/media/getting-started-07-plot-window.png)

対話型ウィンドウでは、履歴の確認、ワークスペースの読み込みと保存、デバッガーへのアタッチ、およびショートカットのコピー/貼り付け操作でソース コード ファイルとの対話を行うこともできます。 詳細については、「[Working with the R Interactive Window](interactive-repl.md)」 (対話型ウィンドウでの作業) を参照してください。

## <a name="experience-code-editing-features"></a>コード編集機能の体験

上記の対話型ウィンドウでの簡単な作業では、コード エディターでも動作する IntelliSense などの基本的な編集機能を紹介しました。 以前と同じコードを入力すると、同じオート コンプリートおよび IntelliSense のメッセージ画面が表示されますが、当然のことながら出力は行われません。

`.R` ファイルにコードを記述すると、すぐにすべてのコードが表示され、簡単にコードのさまざまな部分に小さな変更を行い、対話型ウィンドウでコードをすばやく実行して結果を表示できます。 また、プロジェクトに必要なだけファイルを含めることもできます。 コードがファイル内にある場合は、(後で表示されるように) デバッガーでステップごとに実行することもできます。 これらのすべては、計算アルゴリズムを開発して、1 つ以上のデータセットを操作するためにコードを記述する場合、特にすべての中間結果を確認する必要がある場合に、非常に役立ちます。

例のように、次のステップでは、「[Central Limit Theorem](https://en.wikipedia.org/wiki/Central_limit_theorem)」 (中心極限定理) (Wikipedia) を調査する小さなコードを作成します。 (この例は、Paul Teetor による *R クックブック*から編集されています。)

1. `script.R` エディターで、次のコードを入力します。

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. 結果をすばやく表示するには、すべてのコードを選択し (Ctrl + A キー)、Ctrl + Enter キーを押すか、右クリックして、**[対話型で実行]** を選択します。 この操作を行うと、直接入力したかのように、選択したすべてのコードが対話型ウィンドウに入力され、結果がプロット ウィドウに表示されます。

    ![Visual Studio でのプロットの表示](~/rtvs/media/getting-started-08-plot1.png)

1. 1 行の場合は、いつでも Ctrl + Enter キーを押すだけで、対話型ウィンドウで行を実行できます。

> [!Tip]
> すばやくコードを実行するために、編集を行って Ctrl + Enter キーを押す (または、Ctrl + A キーですべてを選択して Ctrl + Enter キーを押す) パターンについて説明します。 これは、同じ操作のためにマウスを使用するよりもはるかに効率的です。
> 
> さらに、Visual Studio フレームの外部にあるプロット ウィンドウにドラッグ アンド ドロップし、ディスプレイ上の他の目的の場所に配置できます。 これにより、必要なサイズにプロット ウィンドウのサイズを簡単に変更し、画像または PDF ファイルに保存できます。

1. 追加のコード行を少し追加して、2 つ目のプロットを含めます。

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))    
    lines(density(samp.means))
    ```

1. もう一度 Ctrl + A キーと Ctrl + Enter キーを押し、コードを再実行して以下を生成します。

    ![Visual Studio での更新されたデュアル プロット](~/rtvs/media/getting-started-09-plot2.png)

1. 問題は、最初のプロットで垂直スケールが決定されるため、2 つ目のプロット (`lines` を含む) が収まらないことです。 これを修正するには、`plot` 呼び出しに `ylim` パラメーターを設定する必要がありますが、垂直方向の最大値を計算するには、適切にコードを追加する必要があります。 `plot` を呼び出す前に `samp.means` を使用するように、コードを再配置する必要があるため、対話型ウィンドウで 1 行ずつ実行するのは少し不便です。 コード ファイルで、簡単に適切な編集を行うことができます。

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. もう一度 Ctrl + A キーと Ctrl + Enter キーを押すと、結果が表示されます。

    ![適切にスケーリングされた Visual Studio の最新のデュアル プロット](~/rtvs/media/getting-started-10-plot3.png)

エディターで操作できる内容は他にもあります。 詳細については、「[コードの編集](code-editing.md)」、「[IntelliSense](code-intellisense.md)」、および「[コード スニペット](code-snippets.md)」を参照してください。

## <a name="debugging-your-code"></a>コードのデバッグ

Visual Studio の主な強みの 1 つは、デバッグ UI です。 RTVS は、この強力な基盤の上にビルドされ、革新的な UI ([変数エクスプローラー、データ テーブル ビューアー](variable-explorer.md)など) を追加します。 ここでは、デバッグの概要を確認します。

1. 最初に、**[R Tools] > [セッション] > [リセット]** メニューを使用して、現在のワークスペースをリセットし、ここまでに実行したすべてをクリアします。 既定では、対話型ウィンドウで行うすべてが、現在のセッションに入り、これはデバッガーでも使用されます。 セッションをリセットして、既存データのないデバッグ セッションを開始できるようにします (これが目的の操作の場合)。 ソース ファイルはワークスペースの外部で管理および保存されるため、`script.R` ソース ファイルには影響しないことに注意してください。

1. 前のセクションで作成された `script.R` ファイルを使用して、行にブレークポイントを設定します。行にキャレットを配置して F9 キーを押すか、**[デバッグ] > [ブレークポイントの設定/解除]** メニューを選択すると、この行は `pop <-` で開始されます。 左側の余白をクリックすると、1 つのステップでこの操作を行うことができます。この行には、赤いブレークポイントのドットが表示されます。

    ![エディターでのブレークポイントの設定](~/rtvs/media/getting-started-11-debug1.png)

1. ツール バーの **[Source startup file]\(ソース スタートアップ ファイル\)** ボタンを選択するか、**[デバッグ] > [Source startup file]\(ソース スタートアップ ファイル\)** メニュー アイテムを選択するか、F5 キーを押すかのいずれかを行って、`script.R` のコードでデバッガーを起動します。 この操作を行うと、Visual Studio がデバッグ モードに入り、コードの実行が開始されます。 ただし、ブレークポイントを設定した行で停止します。

    ![Visual Studio デバッガーのブレークポイントでの停止](~/rtvs/media/getting-started-12-debug2.png)

1. デバッグ中に、Visual Studio では、1 行ずつコードをステップ実行する機能が提供されます。これには、関数のステップ実行、ステップ オーバー、または呼び出しコンテキストにステップ アウトを行う機能を含まれます。 これらの機能は、他の機能と共に **[デバッグ]** メニューに表示されます (エディターのコンテキスト メニューを右クリックして、[デバッグ] ツール バーを選択)。

    ![Visual Studio のデバッグ ツール バー](~/rtvs/media/getting-started-13-debug3.png)

1. ブレークポイントで停止すると、変数の値を調べることができます。 Visual Studio で **[自動変数]** ウィンドウを検索して、**[ローカル]** という名前の下部のタブを選択します。 **[ローカル]** ウィンドウには、プログラムの現在の位置でローカル変数が表示されます。 前に設定したブレークポイントで停止した場合、`pop` 変数がまだ定義されていないことがわかります。 **[デバッグ] > [ステップ オーバー]** (F10) を使用すると、ポップアップ表示に値が表示されます。

    ![Visual Studio の [ローカル] ウィンドウ](~/rtvs/media/getting-started-14-debug4.png)

1. さまざまなスコープ (グローバル スコープとパッケージ スコープを含む) で変数を調べるには、次のように [[変数エクスプローラー]](variable-explorer.md) を使用します。 また、変数エクスプローラーでも、並べ替え可能な列を含む表形式ビューに切り替え、CSV ファイルにデータをエクスポートする機能が提供されます。

    ![変数エクスプローラーの展開ビュー](~/rtvs/media/variable-explorer-expanded-results.png)

1. 引き続き 1 行ずつプログラムをステップ実行したり、**[続行]** (F5) を選択して完了 (次のブレークポイント) まで実行したりすることができます。

さらに詳細を確認するには、「[デバッグ](debugging.md)」と「[変数エクスプローラー](variable-explorer.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、Visual Studio で対話型ウィンドウを使用して、コードの編集およびデバッグを行い、R プロジェクトの基本について学習しました。 その他の機能を引き続き確認するには、次のトピック、および目次の内容を参照してください。

- [サンプル プロジェクト](getting-started-samples.md)
- [コードの編集](code-editing.md)
- [デバッグ](debugging.md)
- [ワークスペース](workspaces.md)
- [データの視覚化](visualizing-data.md)

