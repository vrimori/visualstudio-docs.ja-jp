---
title: "Visual Studio での編集の概要 | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: fd24e4ebcdda7a3b8fbc0b992e1ef952a930029a
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2018
---
# <a name="quickstart-coding-in-the-editor"></a>クイックスタート: エディター内のコーディング

この 10 分間のエディターの紹介では、ファイルにコードを追加した上で、Visual Studio でコードを記述、コード内を移動、およびコードを理解する簡単な方法をいくつか説明します。

## <a name="create-a-new-code-file"></a>新しいコード ファイルを作成する

新しいファイルを作成し、何らかのコードをそのファイルに追加することから始めます。 エディターが提供している一部の特典は、プロジェクトを作成しなくても利用できます。

1. Visual Studio を開き、メニュー バーの **[ファイル]** メニューから、**[新規作成]** > **[ファイル]** を選択します。

1. **[新しいファイル]** ダイアログ ボックスの **[全般]** カテゴリで、**[Visual C# クラス]** を選択し、**[開く]** を選択します。

   エディターで新しいファイルが開かれ、C# クラスのスケルトンが表示されます。

## <a name="using-code-snippets"></a>コード スニペットの使用

Visual Studio で提供されている便利なコード スニペットを使用すると、一般的に使用されるコード ブロックを迅速かつ簡単に生成することができます。 [コード スニペット](../ide/code-snippets.md)は、C#、Visual Basic、C++ など、さまざまなプログラミング言語で使用することができます。 C# `void Main` スニペットをファイルに追加してみましょう。

1. `Class1` コンストラクターの右中かっこの下にカーソルを置き、文字 `svm` を入力します。

   `svm` スニペットに関する情報を含んだ IntelliSense ダイアログ ボックスが表示されているのがわかります。

   ![Intellisense スニペット](media/quickstart-intellisense-snippet.png)

1. **Tab** キーを 2 回押すと、コード スニペットが挿入されます。

   `static void Main()` メソッドの署名がファイルに追加されているのがわかります。 `Main()` メソッドは、C# アプリケーションのエントリ ポイントです。

利用できるコード スニペットは、言語によって異なります。 目的のプログラミング言語で使用可能なコード スニペットを確認するには、**[編集]**、**[IntelliSense]**、**[スニペットの挿入]** の順に選択し、言語のフォルダーを選択します。 C# の場合、リストは次のようになります。

![C# コード スニペットのリスト](media/quickstart-code-snippet-list.png)

このリストには、クラス、コンストラクター、`Console.WriteLine()`、`for` ループ、`if` ステートメント、`switch` ステートメントなどを作成するためのスニペットが含まれています。

## <a name="commenting-out-code"></a>コードのコメント アウト

ツールバーには、コード作成時の生産性を高めるためのボタンが複数用意されています。 たとえば、IntelliSense 完了モードの切り替え、インデントの増減、ブックマークの設定、コードのコメント アウトを行うことができます。 このセクションでは、コンパイルしたくないコードをコメント アウトします。

![エディターのツール バー](media/quickstart-editor-toolbar.png)

1. `Main()` メソッド本体に次のコードを貼り付けます。

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    }

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. `morewords` 変数は現在使用していませんが、後で使用するかもしれないので、削除したくありません。 そこで、これらの行をコメント アウトしましょう。 終了セミコロンまでの `morewords` の定義全体を選択し、ツールバーの **[選択された行をコメント アウトします。]** ボタンを選択します。あるいは、**Ctrl**+**K** キー、**Ctrl**+**C** キーを押します。

   ![コメント アウト ボタン](media/quickstart-comment-out.png)

   選択した各列の先頭に C# コメント文字 `//` を追加すると、コードがコメント アウトされます。

## <a name="collapsing-code-blocks"></a>コード ブロックを折りたたむ

生成された `Class1` の空のコンストラクターは表示したくありません。コードのビューを整理するために、ビューを折りたたみましょう。 コンストラクターの最初の行の余白にある、内部にマイナス記号が表示された小さな灰色のボックスを選択します。 または、キーボードを使用している場合は、コンストラクター コード内の任意の場所にカーソルを置き、**Ctrl**+**M** キー、**Ctrl**+**M** キーを押します。

![アウトライン折りたたみボタン](media/quickstart-collapse.png)

コード ブロックが最初の行に折りたたまれ、後続に省略記号 (`...`) が表示されます。 コード ブロックを再度展開するには、現在内部にプラス記号が表示されている同じ灰色のボックスをクリックするか、**Ctrl**+**M** キー、**Ctrl**+**M** キーをもう一度押します。 これは、[アウトライン](../ide/outlining.md)機能と呼ばれ、長いメソッドまたはクラス全体を折りたたむ場合に特に便利です。

## <a name="viewing-symbol-definitions"></a>シンボル定義の表示

Visual Studio エディターでは、型やメソッドなどの定義の検査を容易に行うことができます。1 つの方法として、たとえば、シンボルが参照されている任意の場所で **[定義へ移動]** を選択して、定義を含むファイルに移動します。 作業中のファイルからフォーカスを移動しないより迅速な方法としては、[[定義をここに表示]](../ide/go-to-and-peek-definition.md#peek-definition) を使用します。 `string` の定義を参照してみましょう。

1. `string` が出現している箇所を右クリックし、コンテンツ メニューから **[定義をここに表示]** を選択するか&mdash;、または **Alt**+**F12** キーを押します。

   `String` クラスの定義を含むポップアップ ウィンドウが表示されます。 ポップアップ ウィンドウ内をスクロールすることも、参照しているコードから別の種類の定義を参照することもできます。

   ![コード定義ウィンドウ](media/quickstart-peek-definition.png)

1. 表示された定義ウィンドウを閉じるには、ポップアップ ウィンドウの右上にある、内部に "x" が表示された小さなボックスを選択します。

## <a name="using-intellisense-to-complete-words"></a>IntelliSense を使用した入力補完

コードを記述する場合、[IntelliSense](../ide/using-intellisense.md) は貴重なリソースです。 このリソースでは、使用可能な型のメンバーに関する情報、またはメソッドの各種オーバーロードのためのパラメーターの詳細を表示できます。 また、IntelliSense を使用すると、単語を区別するために十分な文字を入力した後に入力補完を利用することができます。 順序付けされた文字列をコンソール ウィンドウに出力するコード行を追加してみましょう。

1. `query` 変数の下で、次のコードの入力を開始します。

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense が `query` シンボルに関する**クイック ヒント**を表示しているのがわかります。

   ![IntelliSense の入力候補](media/quickstart-intellisense-completion-list.png)

1. IntelliSense の "入力候補" 機能を使用して単語 `query` の残りを挿入するには、**Tab** キーを押します。

1. 次のコードのように、コード ブロックを完成させます。 コード スニペットを使用して再度実行することもできます。それには、`cw` を入力してから、**Tab** キーを 2 回押して、`Console.WriteLine` コードを生成します。

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactoring-a-name"></a>名前のリファクタリング

だれも最初から適切なコードは記述できないものです。変更を必要とする可能性のある要素の 1 つに、変数またはメソッドの名前があります。 Visual Studio の[リファクタリング](../ide/refactoring-in-visual-studio.md)機能を使用して、`_words` 変数の名前を `words` に変更してみましょう。

1. `words` 変数の定義にカーソルを置き、右クリックまたはコンテキスト メニューから **[名前の変更]** を選択するか、**Ctrl**+**R** キー、**Ctrl**+**R** キーを押します。

   エディターの右上に **[名前の変更]** ダイアログ ボックスがポップアップ表示されます。

1. 目的のファイル名 `words` を入力します。 クエリ内の `words` への参照も名前が自動的に変更されることに注意してください。 **Enter** キーを押す前に、**[名前の変更]** ポップアップ ボックスで **[コメントを含める]** チェック ボックスを選択します。

   ![[名前の変更] ダイアログ ボックス](media/quickstart-rename.png)

1. **Enter** キーを押します。

   `words` の出現箇所とコード コメント内の `words` への参照箇所の両方で名前が変更されました。

## <a name="next-steps"></a>次の手順

Visual Studio エディターにおけるこのクイックスタートは完了しました。 次に、Visual Studio IDE の他のクイックスタートを試してみる、[コード内を移動](../ide/navigating-code.md)する他の方法を参照する、またはこれまで見てきた機能の詳細情報へのリンクを確認することができます。 または他の方法でコーディングをお楽しみください。

## <a name="see-also"></a>関連項目

[クイックスタート: Visual Studio IDE の表示の紹介](../ide/quickstart-ide-orientation.md)  
[クイックスタート: Visual Studio IDE とエディターのカスタマイズ](../ide/quickstart-personalize-the-ide.md)  
[クイック スタート: プロジェクトとソリューション](../ide/quickstart-projects-solutions.md)  
[コード スニペット](../ide/code-snippets.md)  
[アウトライン](../ide/outlining.md)  
[[定義へ移動] と [定義をここに表示]](../ide/go-to-and-peek-definition.md)  
[リファクタリング](../ide/refactoring-in-visual-studio.md)  
[IntelliSense の使用](../ide/using-intellisense.md)