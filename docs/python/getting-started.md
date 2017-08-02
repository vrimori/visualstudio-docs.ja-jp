---
title: "Visual Studio での Python の概要 | Microsoft Docs"
ms.custom: 
ms.date: 5/1/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9087b19-275b-4cc1-8d0c-f9c4356c9ce8
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 8001036077b8b14af80fabceafad5d3aff9b25f4
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---

# <a name="getting-started-with-python-in-visual-studio"></a>Visual Studio での Python の概要

Visual Studio と Python ワークロード (Visual Studio 2017 の場合) または Python Tools for Visual Studio (Visual Studio 2015 以前の場合) をインストールしたら、さっそく Python での開発を体験してみましょう。 (必要に応じて「[インストール](installation.md)」を参照してください。)

このチュートリアルでは、新しい空の Python アプリケーションを作成し、使用する Python 環境を選択します。次に、コードをいくつか記述して IntelliSense の動作を確認します。 その後、対話型 REPL ウィンドウを少しの間使用してさらにコードを作成し、プログラムを完成させたら、プログラム自体とデバッガーの両方で実行します。

> [!Note]
> このチュートリアルでは、Visual Studio 2017 での Python 開発について説明しています。他のバージョンでも手順はほぼ同じですが、細部は異なる場合があります。

## <a name="create-a-new-python-project"></a>新しい Python プロジェクトを作成する

Visual Studio の Python サポートには多数の[プロジェクト テンプレート](python-projects.md)が含まれており、Bottle、Flask、および Django フレームワークと Azure Cloud Services を使用した Web アプリケーションなど、さまざまな種類のプロジェクトを開始できるようになっています。 ただし、このチュートリアルでは、空のプロジェクトを作成することから始めます。

1. Visual Studio で **[ファイル] > [新しいプロジェクト]** を選択し、**[新しいプロジェクト]** ダイアログを開きます。 ここでテンプレートを参照して選択し、プロジェクトを作成するフォルダーを指定できます。

1. Python テンプレートを探すには、左側で **[テンプレート] > [他の言語] > [Python]** を選択するか、"Python" と入力して検索します。

    ![Python プロジェクトが表示されている [新しいプロジェクト] ダイアログ](~/python/media/getting-started-new-project.png)

1. "Python Application" テンプレートを選択し、プロジェクトのフォルダーを指定して、**[OK]** を選択します (同時にプロジェクトのローカル リポジトリも作成する場合は、**[ソース管理に追加]** オプションを選択します)。

    > [!Tip]
    > "From exiting Python Code" テンプレートを使用すると、新しい空のプロジェクトを作成して既存のコードをインポートする代わりに、既に Python コードが格納されているフォルダーから Visual Studio プロジェクトをすばやく作成することができます。

1. しばらくすると、Visual Studio ソリューション エクスプローラー ウィンドウにプロジェクトが開きます。 ここでプロジェクトのファイルやフォルダーを参照したり、環境を管理したりできます。

    ![Python プロジェクトが表示されたソリューション エクスプローラー](~/python/media/getting-started-solution-explorer-1.png)

1. **[Python Environments (Python 環境)]** ノードを展開すると、このプロジェクトに現在既定でインストールされている Python インタープリターが表示されます。 そのインタープリター ノードも展開すると、その環境で使用できるライブラリの一覧が表示されます。

    ![Python 環境を表示するソリューション エクスプローラー](~/python/media/getting-started-solution-explorer-2.png)

1. Visual Studio 2015 以前を使用している場合、既定でインストールされている Python インタープリターはありません。 このプロセスについては、「[selecting and installing a Python interpreter (Python インタープリターの選択とインストール)](python-environments.md#selecting-and-installing-python-interpreters)」を参照してください。

### <a name="going-deeper"></a>詳しい説明

- [Visual Studio の Python プロジェクト](python-projects.md)
- [Web プロジェクト テンプレート](template-web.md)
- [Django Web プロジェクト テンプレート](template-django.md)
- [Azure クラウド サービス テンプレート](template-azure-cloud-service.md)

## <a name="writing-and-running-code"></a>コードを記述して実行する

1. 新しい "Python Application" プロジェクトを作成すると、Visual Studio エディターで既定の `PythonApplication1.py` という名前の空のファイルが開きます。 この名前を変更するには、ソリューション エクスプローラーでファイルを右クリックして **[名前を変更]** を選択し、名前を `hello.py` に変更します。

1. `print("Hello world")` の入力を開始します。入力の途中で、Visual Studio IntelliSense のオートコンプリートのオプションが表示される様子に注目してください。 ドロップダウン リストで四角で囲まれたオプションは既定の入力候補で、Tab キーを押して使用します。 オートコンプリートは、長いステートメントや識別子を記述する場合に非常に便利です。

    ![IntelliSense オートコンプリートのポップアップ](~/python/media/getting-started-coding-1.png)

1. IntelliSense では、使用しているステートメントや呼び出している関数などに応じて、異なる情報が表示されます。 `print` 関数に続けて `(` と入力すると、この関数のすべての使用法がポップアップ表示され、さらに、指定する必要がある現在の引数が太字で表示されます (次の図では **value**)。

    ![IntelliSense オートコンプリートの関数のポップアップ](~/python/media/getting-started-coding-2.png)

1. 次と同じステートメントを完成させます。

  ```python
  print("Hello world")
  ```

1. このコードを実行するには、ツールバーの **[開始]** ボタン (下図を参照) をクリックするか、F5 キーを押すか、**[デバッグ] > [デバッグの開始]** メニュー項目を選択します。

    ![[デバッグ] ツールバーの [開始] ボタン](~/python/media/getting-started-coding-3.png)

    > [!Note]
    > Visual Studio 2015 以前では、インタープリターは既定でインストールされていません。インタープリターがないというメッセージが表示される場合は、「[selecting and installing a Python interpreter (Python インタープリターの選択とインストール)](python-environments.md#selecting-and-installing-python-interpreters)」を参照してください。

1. Visual Studio がプロジェクトの既定の環境を使用してコードを実行し、コマンド ウィンドウに結果を表示します。 任意のキーを押すと、ウィンドウが閉じて、デバッグ セッションが終了します。

    ![[デバッグ] ツールバーの [開始] ボタン](~/python/media/getting-started-coding-4.png)

1. IntelliSense では、ステートメントと関数に加え、`import` ステートメントの入力候補も表示されます。 これにより、自分の環境で使用できるモジュールと、そのモジュールで使用できるメンバーを簡単に見つけることができます。 エディターで `print` 行を削除し、`import` と入力します。 すると、モジュールの一覧が表示されます。

    ![import ステートメントで使用できるモジュールを示す IntelliSense](~/python/media/getting-started-coding-5.png)

1. `sys` と入力するか選択して、行を完成させます。

1. 次の行に `from` と入力し、もう一度モジュールの一覧を表示します。

    ![from ステートメントで使用できるモジュールを示す IntelliSense](~/python/media/getting-started-coding-6.png)

1. `math` を選択するか入力し、続けてスペースと `import` を入力すると、モジュールのメンバーが表示されます。

    ![モジュールのメンバーを表示する IntelliSense](~/python/media/getting-started-coding-7.png)

1. 利用できるオートコンプリートのオプションを確認し、メンバー `sin`、`cos`、`radians` インポートして完了します。 完了すると、コードは次のようになります。

  ```python
  import sys  
  from math import sin, cos, radians          
  ```

> [!Tip]
> 入力候補は、入力中の部分文字列、単語の一致部分、単語の先頭の文字、および省略された文字で機能します。 詳細については、「[Editing Code - Completions (コードの編集 - 入力候補)](code-editing.md#completions)」を参照してください。

次の手順では、対話型 REPL ウィンドウを使用して、デバッガーを実行せずにすぐにテストできるコードを記述します。

### <a name="going-deeper"></a>詳しい説明

- [コードの編集](code-editing.md)
- [コードの書式設定](code-formatting.md)
- [コードのリファクタリング](code-refactoring.md)
- [PyLint の使用](code-pylint.md)


## <a name="using-the-interactive-repl-window"></a>対話型 REPL ウィンドウを使用する

Python 用の Visual Studio 対話型ウィンドウは、機能豊富な REPL (読み取り、評価、出力、ループ) エクスペリエンスを提供し、通常の編集、ビルド、デバッグのサイクルを大幅に短縮します。 これは Python コマンドラインの REPL エクスペリエンスに似ていますが、この後説明するように、いくつかの追加機能があります。

1. Visual Studio のメイン メニューで、**[表示] > [その他のウィンドウ] > [Python Interactive Windows (Python Interactive ウィンドウ)]** を選択して対話型ウィンドウを開きます。 ウィンドウが開き、通常の Python REPL プロンプト ”>>>” が表示されます。 環境は、ツールバーのドロップダウン メニューを使用していつでも変更できます。

    ![Python Interactive ウィンドウ](~/python/media/getting-started-interactive-1.png)

1. ステートメント (`print("hello")` など) や式 (`123/567` など) をいくつか入力して、すぐに表示される結果を確認します。

    ![Python Interactive ウィンドウの即時の結果](~/python/media/getting-started-interactive-2.png)

1. 関数の定義など、複数のステートメントの記述を開始すると、Interactive ウィンドウに行の継続を表す ”...” プロンプトが表示されます。コマンドライン REPL とは異なり、自動でインデントされます。

    ![ステートメントの継続を示す Python Interactive ウィンドウ](~/python/media/getting-started-interactive-3.png)

1. Interactive ウィンドウでは、入力内容がすべて履歴に残されます。複数行の履歴項目により、コマンドライン REPL の機能が強化されています。 たとえば、関数を行ごとに再作成するのではなく、上の `f` 関数の定義全体を単一ユニットとして呼び出して、名前を `make_double` に変更することが簡単にできます。

1. もう 1 つの非常に便利な機能として、エディター ウィンドウから Interactive ウィンドウに複数行のコードをすばやく送信し、高速の REPL 環境でそのコードを実行できます。デバッガーで実行するために別にコードを記述する必要はありません。 これを行うには、まず、エディターで開かれている hello.py ファイルに次のコードを追加します。

  ```python
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'
  ```

1. hello.py のすべてのコード (`import` ステートメントを含む) を選択し、右クリックして **[Interactive に送信]** を選択します (または Ctrl + Enter キーを押します)。 コードがすぐに Interactive ウィンドウに貼り付けられて、実行されます。 このコードでは関数を定義しているため、この関数を数回呼び出すことですばやくテストすることができます。

    ![Interactive ウィンドウへのコードの送信](~/python/media/getting-started-interactive-4.png)

1. **[Interactive に送信]** コマンドを使用すると、(たとえばオンラインで見つけた) 複数行のコードを効率よく対話型ウィンドウに貼り付けることができます (対話型ウィンドウに直接コードを貼り付けることはできません)。 たとえば、次のコードをコピーして Interactive ウィンドウに貼り付けようとしても (Ctrl + V キーを押しても) 何も起こりませんが、 エディターに貼り付けてから選択し、**[Interactive に送信]** コマンドを使用することで、コードが実行する様子を確認することができます。

  ```python
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

    ![[Interactive に送信] を使用した複数行のコードの貼り付け](~/python/media/getting-started-interactive-5.png)

1. 前に説明したように、関数の定義は単一ユニットとして REPL の履歴に残るため、簡単に関数に戻って変更を加え、再テストすることができます。

1. 満足のいくコードができたら、Interactive ウィンドウでコードを選択し、右クリックして **[コードのコピー]** を選択してから、エディターに貼り付けます。 **[コードのコピー]** コマンドには、プロンプト テキスト (>>> や ...) 以外に、出力も自動的に除外する特別な機能があります。 たとえば、下の図に示す範囲を選択してこのコマンドを使用すると...

  ![Interactive ウィンドウの [コードのコピー] コマンド](~/python/media/getting-started-interactive-6.png)

  次のようにコードのみが貼り付けられます。

  ```python
  make_dot_string(180)
  make_dot_string(135)
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

1. 最後に、Interactive ウィンドウには多くのメタコマンドがあり、ファイルを読み込んだり、履歴を保持したまま環境をリセットしたり、コメントを挿入したりできます。 詳細については、「[Interactive Windows - meta-commands (Interactive ウィンドウ - メタコマンド)](interactive-repl.md#meta-commands)」を参照してください。

### <a name="going-deeper"></a>詳しい説明

- [Interactive ウィンドウの使用](interactive-repl.md)
- [IPython REPL の使用](interactive-repl-ipython.md)

## <a name="running-code-in-the-debugger"></a>デバッガーでコードを実行する

Visual Studio は、プロジェクト管理、豊富な編集機能、対話型ウィンドウに加え、Python コード用のフル機能のデバッグ サポートも提供しています。

1. hello.py ファイルを編集し、次と同じコードを作成します。

  ```python  
  from math import sin, cos, radians  
  import sys  
    
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
    
  def main():  
      for i in range(360 * 5):
          s = make_dot_string(i)  
          print(s)  
            
  main()
  ```  

1. コードが正常に機能することを確認します。それには、ツールバーの **[開始]** をクリックするか、F5 キーを押すか、または **[デバッグ] > [デバッグの開始]** メニュー コマンドを選択します。 デバッガーでコードが実行されますが、ブレークポイントを設定していないので、単にイテレーションの波のパターンが出力されます。 この時点で任意のキーを押すと、出力ウィンドウが閉じます。

    > [!Tip]
    > プログラムが完了したときに出力ウィンドウを自動的に閉じるには、`main()` の呼び出しを次のコードに置き換えます。
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```
    > 
    > または、出力ウィンドウが閉じないようにしたい場合に自動的に閉じてしまうときは、プロジェクトを右クリックし、**[プロパティ]** の **[デバッグ]** タブを選んで、**[インタープリターの引数]** フィールドに `-i` を追加します。 このようにすると、プログラム完了後にインタープリターは対話モードになり、ユーザーが Ctrl + Z キー、Enter キーの順に押して終了するまで、ウィンドウは開いたままになります。

1. `main` 関数の最初の行にブレークポイントを設定します。それには、行の左側の灰色の余白をクリックするか、行にキャレットを配置して *[デバッグ] > [ブレークポイントの設定/解除]** コマンドを使用します (または F9 キーを押します)。 灰色の余白に、ブレークポイントを示す赤い点が表示されます (下図の青い矢印の先)。

    ![ブレークポイントの設定](~/python/media/getting-started-debugging-1.png)

1. デバッガーをもう一度開始すると、ブレークポイントを設定した行でコードの実行が停止します。 ここで、呼び出し履歴を確認したり、ローカル ウィンドウでローカル変数を調べたりすることができます。

    ![Python のブレークポイント UI エクスペリエンス](~/python/media/getting-started-debugging-2.png)

1. `for` ループのイテレーションを 1 行ごとにステップ実行します。それには、F10 キーを押すか、**[デバッグ] > [ステップ オーバー]** コマンドを選択するか、または [ステップ オーバー] ツールバー ボタンをクリックします。 これは、デバッガーが `make_dot_string` の各呼び出しを実行するものの、(ブレークポイントを設定していない限りは) この関数の内部では停止しないことを意味します。

1. ツールバーには、次の図に示すように 3 つのステップ実行ボタンがあります。左から順に、[ステップ イン]、[ステップ オーバー]、[ステップ アウト] です。

    ![ツールバーのステップ実行ボタン](~/python/media/getting-started-debugging-3.png)

1. [ステップ イン] コマンド (F11 キー) を使用して `make_dot_string` にステップ インします。 `for` ループからその関数にステップ インするのがわかります。 もう一度ステップ実行すると `for` ループに戻りますが、関数に他にも行があった場合はそれらも 1 行ずつステップ実行されます。 関数の残りの行を実行してから呼び出し元のコードに戻るには、[ステップ アウト] コマンド (Shift + F11 キー) を使用します。

1. 次のブレークポイントに到達するまで (またはプログラムが終了するまで) コードの実行を続けるには、もう一度 F5 キーを押すか、ツール バーの **[続行]** ボタンをクリックするか、または **[デバッグ] > [続行]** を選択します。 `for` ループにブレークポイントを設定しているので、次のイテレーションで中断します。

1. ループの何百ものイテレーションをステップ実行するのは大変なので、`i` の値が特定の値 (たとえば 1600 など) を超えた場合にのみ中断するよう、設定したブレークポイントに条件を追加することができます。 これを行うには、ブレークポイントの赤い点を右クリックして **[条件]** を選択します。 表示された [ブレークポイント設定] ウィンドウで、式として `i > 1600` と入力し、**[閉じる]** を選択します。 F5 キーを押して続行します。プログラムは、次に中断されるまでしばらくの間実行します。 

    ![ブレークポイント条件の設定](~/python/media/getting-started-debugging-4.png)

1. プログラムを完了するには、ブレークポイントの設定/解除を再度切り替えて、F5 キーを押します。 デバッグが完了すると、Visual Studio が編集モードに戻ります。

### <a name="going-deeper"></a>詳しい説明

- [デバッグ](debugging.md)
- 「[Debugging in Visual Studio (Visual Studio でのデバッグ)](../debugger/debugging-in-visual-studio.md)」で、Visual Studio のデバッグ機能の完全なドキュメントも参照してください。

## <a name="next-steps"></a>次のステップ

上の「詳しい説明」リンクに加え、Visual Studio での Python 開発のその他の機能について説明している次のトピックも参照してください。

- Visual Studio から Azure App Service に接続する方法については、「[Publishing a Python web application to Azure (Azure への Python Web アプリケーションの発行)](publishing-to-azure.md)」を参照してください。
- 仮想環境を含めたさまざまな環境をグローバルに、または個々のプロジェクトごとに管理する方法については、「[Python Environments (Python 環境)](python-environments.md)」を参照してください。
- Visual Studio では、リモート サーバー上のアプリケーションのデバッグも可能です。詳しくは、「[クロスプラットフォーム リモート デバッグ](debugging-cross-platform-remote.md)」と「[Azure リモート デバッグ](debugging-azure-remote.md)」を参照してください。
- [Visual Studio プロファイリング](profiling.md)を使用して、Python コードのパフォーマンスを評価できます。
- 「[Unit Testing (単体テスト)](unit-testing.md)」で説明したように、Python で記述された単体テストは、Visual Studio テスト エクスプローラーと直接統合されます。
- [Microsoft Virtual Academy の無料 Python コース](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)

