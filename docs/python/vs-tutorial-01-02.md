---
title: "Visual Studio での Python の使用、手順 2 | Microsoft Docs"
ms.custom: 
ms.date: 10/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: d417ac531331b62b0f711fe155a94f1ac0954310
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="step-2-writing-and-running-code"></a>手順 2: コードを記述して実行する

**前の手順: [Python プロジェクトを作成する](vs-tutorial-01-01.md)**

ソリューション エクスプローラーがプロジェクト ファイルを管理する場所であるのに対し、*エディター* ウィンドウは通常、ファイルの*コンテンツ* (ソース コードなど) を操作する場所です。 エディターは編集中のファイルの種類 を、プログラミング言語 (ファイル拡張子に基づく) などの状況から認識し、構文の色分け表示やオートコンプリートなど、その言語に適した機能を IntelliSense を使用して提供します。

1. 新しい "Python Application" プロジェクトを作成すると、Visual Studio エディターで既定の `PythonApplication1.py` という名前の空のファイルが開きます。 

1. エディターで `print("Hello, Visual Studio")` の入力を開始します。入力の途中で、Visual Studio IntelliSense のオートコンプリートのオプションが表示される様子に注目してください。 ドロップダウン リストで四角で囲まれたオプションは既定の入力候補で、Tab キーを押して使用します。 入力候補は、長いステートメントや識別子を記述する場合に非常に便利です。

    ![IntelliSense オートコンプリートのポップアップ](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense では、使用しているステートメントや呼び出している関数などに応じて、異なる情報が表示されます。 `print` 関数で、`print` の後に `(` を入力することで、関数呼び出しでその関数のすべての使用情報を表示することを示します。 IntelliSense のポップアップにも、(この例の **value** ように) 現在の引数が太字で示されます。

    ![IntelliSense オートコンプリートの関数のポップアップ](media/vs-getting-started-python-05-IntelliSense2b.png)

1. 次と同じステートメントを完成させます。

    ```python
    print("Hello, Visual Studio")
    ```

1. ステートメント `print` を引数 `"Hello Visual Studio"` と区別する構文配色機能に注目してください。 また、文字列の最後の `"` を一時的に削除し、Visual Studio が構文エラーが含まれるコードに対して赤色の下線を表示することに注目してください。 次に、`"` を置換してコードを修正します。
 
    ![IntelliSense の構文の色分け表示とエラーの強調表示](media/vs-getting-started-python-06-IntelliSense3b.png)
 
    > [!Tip]
    > 開発環境は非常に個人的な問題であるため、Visual Studio では Visual Studio の外観と動作の完全な制御が提供されています。 **[ツール] > [オプション]** メニュー コマンドを選択し、**[環境]** と **[テキスト エディター]** タブの下の設定を調べます。 既定では限られた数のオプションしか表示されません。すべてのプログラミング言語のすべてのオプションを表示するには、ダイアログ ボックスの下部で **[すべての設定を表示]** を選択します。 

1. Ctrl キーを押しながら F5 キーを押すか、**[デバッグ] > [デバッグの開始]** メニュー項目を選択して、このポイントまでに書き込んだコードを実行します。 コードにエラーがまだある場合は、Visual Studio によって警告されます。
 
1. プログラムを実行すると、コマンド ラインから `PythonApplication1.py` を使用して Python インタープリターを実行した場合と同じように、結果を示すコンソール ウィンドウが表示されます。 キーを押してウィンドウを閉じ、Visual Studio エディターに戻ります。

    ![プログラムの最初の実行の出力](media/vs-getting-started-python-07-output.png)

1. IntelliSense では、ステートメントと関数の補完に加え、Python `import` および `from` ステートメントの入力候補も表示されます。 これらの補完は、自分の環境で使用できるモジュールと、そのモジュールで使用できるメンバーを簡単に見つけることに役立ちます。 エディターで `print` 行を削除し、`import ` と入力します。 スペースを入力すると、モジュールのリストが表示されます。

    ![import ステートメントで使用できるモジュールを示す IntelliSense](media/vs-getting-started-python-08-import1.png)

1. `sys` と入力するか選択して、行を完成させます。

1. 次の行に `from` と入力し、もう一度モジュールの一覧を表示します。

    ![from ステートメントで使用できるモジュールを示す IntelliSense](media/vs-getting-started-python-09-import2.png)

1. `math` を選択するか入力し、続けてスペースと `import` を入力すると、モジュールのメンバーが表示されます。

    ![モジュールのメンバーを表示する IntelliSense](media/vs-getting-started-python-10-import3.png)

1. 利用できるオートコンプリートのオプションを確認し、メンバー `sin`、`cos`、`radians` インポートして完了します。 完了すると、コードは次のようになります。

    ```python
    import sys  
    from math import sin, cos, radians          
    ```

    > [!Tip]
    > 入力候補は、入力中の部分文字列、単語の一致部分、単語の先頭の文字、および省略された文字で機能します。 詳細については、「[Editing Code - Completions (コードの編集 - 入力候補)](code-editing.md#completions)」を参照してください。

1. 360 度のコサイン値を出力するため、もう少しコードを追加します。

    ```python 
    for i in range(360):        
        print(cos(radians(i)))
    ```

1. Ctrl キーを押しながら F5 キーを押すか、**[デバッグ] > [デバッグなしで開始]** を選択して、もう一度プログラムを実行します。 完了したら、出力ウィンドウを閉じます。


## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [対話型 REPL ウィンドウを使用する](vs-tutorial-01-03.md)


## <a name="going-deeper"></a>詳しい説明

- [コードの編集](code-editing.md)
- [コードの書式設定](code-formatting.md)
- [コードのリファクタリング](code-refactoring.md)
- [PyLint の使用](code-pylint.md)
