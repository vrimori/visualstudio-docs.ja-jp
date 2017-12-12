---
title: "Visual Studio の Python 対話型 REPL | Microsoft Docs"
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 0e524208684afa38916af858e6ec3a8adb1f5932
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-the-python-interactive-window"></a>Python 対話型ウィンドウの使用

Visual Studio において各 Python 環境に用意されている対話型の read-evaluate-print loop (REPL) ウィンドウを使うと、コマンド ラインの `python.exe` で実行する REPL が向上します。 (**[表示] > [その他のウィンドウ] > [&lt;環境&gt;インタラクティブ**] メニュー コマンドで開いた) 対話型ウィンドウを使用すると、任意の Python コードを入力し、すぐに結果を確認することができます。 このコーディング方法は、API とライブラリの学習と実習、およびプロジェクトに含める作業コードを対話形式で開発するのに役立ちます。

![Python Interactive ウィンドウ](media/interactive-window.png)

Visual Studio では、複数の Python REPL モードから選ぶことができます。

| REPL | 説明 | 編集 | デバッグ | イメージ |
| --- | --- | --- | --- | --- |
| 標準 | 既定の REPL、Python と直接対話 | 標準的な編集 (複数行など)。 | はい、`$attach` を使用 | いいえ |
| デバッグ | 既定の REPL、デバッグ対象の Python プロセスと対話 | 標準的な編集 | デバッグのみ | いいえ |
| IPython | REPL は IPython のバックエンドと対話 | IPython コマンド、Pylab の利便性 | いいえ | はい、REPL でインライン |
| IPython (Pylab なし) | REPL は IPython のバックエンドと対話 | 標準的な IPython | いいえ | はい、別のウィンドウ | 

このトピックでは、REPL の**標準**モードと**デバッグ** モードのについて説明します。 IPython モードについて詳しくは、「[Using the IPython REPL](interactive-repl-ipython.md)」(IPython REPL の使用) をご覧ください。

Ctrl + Enter などのエディターとの対話を含む、例を使用した詳細なチュートリアルについては、「[チュートリアル手順 3: 対話型 REPL ウィンドウを使用する](vs-tutorial-01-03.md)」を参照してください。 ビデオでの概要については、「[Python 対話型ウィンドウ](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567)」 (Microsoft Virtual Academy、2 分 22 秒) を参照してください。

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567]

## <a name="opening-an-interactive-window"></a>対話型ウィンドウを開く

環境用の対話型ウィンドウを開くにはいくつかの方法があります。

(第 1 の方法) [Python Environments (Python 環境)] ウィンドウに切り替え (**[表示] > [その他のウィンドウ] > [Python Environments (Python 環境)]**、または Ctrl + K、Ctrl + `)、**[Open Interactive Window (対話型ウィンドウを開く)]** コマンドまたは選んだ環境のボタンを選びます。

![Python 環境ウィンドウの対話型ウィンドウへのリンク](media/interactive-window-opening.png)

(第 2 の方法) **[表示] > [その他のウィンドウ]** メニューの下の方に、既定の環境の ** [Python Interactive ウィンドウ]** コマンドと、環境ウィンドウに切り替えるためのコマンドがあります。

![[表示] > [その他のウィンドウ] の対話型ウィンドウ メニュー項目](media/interactive-window-menu.png)

(第 3 の方法) プロジェクトのスタートアップ ファイルで対話型ウィンドウを開くことができます。または、スタンドアロン ファイルの場合は、**[デバッグ] > [Execute [Project | File] in Python Interactive (Python Interactive で [プロジェクト | ファイル] を実行する)]** メニュー コマンドを選びます (Shift + Alt + F5)。

![[Execute Project in Python Interactive (Python Interactive でプロジェクトを実行する)] メニュー](media/interactive-execute-project.png)

(第 4 の方法) ファイルでコードを選び、後で説明する [Interactive にコードを送信するコマンド](#send-code-to-interactive-command)を使います。

## <a name="interactive-window-options"></a>対話型ウィンドウのオプション

**[ツール] > [オプション] > [Python Tools] > [対話型ウィンドウ]** を使って、対話型ウィンドウのさまざまな部分を制御できます ([オプション](options.md)を参照)。

![Python Interactive ウィンドウのオプション](media/options-interactive-windows.png)

## <a name="using-the-interactive-window"></a>対話型ウィンドウの使用

対話型ウィンドウを開いた後は、`>>>` プロンプトで 1 行ずつコードの入力を開始できます。 対話型ウィンドウは、入力と同時に各行を実行します。これには、モジュールのインポートや、変数の定義などが含まれます。

![Python Interactive ウィンドウ](media/interactive-window.png)

例外は、上に示すように、`for` ステートメントがコロンで終わる場合など、完全なステートメントにするために追加のコード行が必要な場合です。 このような場合、行プロンプトが `...` に変わり、ブロックの追加行を入力する必要があることを示します (上の図の 4 番目と 5 番目の行を参照)。 空白行で Enter キーを押すと、対話型ウィンドウはブロックを終了し、インタープリターでブロックを実行します。

> [!Tip]
> 対話型ウィンドウは、囲むスコープに属しているステートメントを自動的にインデントすることにより、Python の通常のコマンドライン REPL エクスペリエンスを向上させます。 対話型ウィンドウの履歴 (上方向キーで再呼び出しされます) は複数行の項目も提供しますが、コマンドライン REPL は単一行しか提供しません。

<a name="meta-commands"></a>また、対話型ウィンドウは複数のメタコマンドもサポートします。 すべてのメタコマンドは `$` で始まり、「`$help`」と入力するとメタコマンドの一覧が表示され、「`$help <command>`」と入力すると特定のコマンドの使用方法の詳細が表示されます。

| メタコマンド | 説明 |
| --- | --- |
| `$$` | コメントを挿入します。セッションのコードにコメントを追加するのに役立ちます。 |
| `$attach` | Visual Studio のデバッガーを REPL ウィンドウ プロセスにアタッチして、デバッグできるようにします。 |
| `$cls`, `$clear` | エディター ウィンドウの内容を消去し、履歴と実行コンテキストはそのまま維持します。 |
| `$help` | コマンドの一覧または特定のコマンドのヘルプを表示します。 |
| `$load` | ファイルからコマンドを読み込み、完了するまで実行します。 |
| `$mod` | 現在のスコープを指定されたモジュール名に切り替えます。 |
| `$reset` | 実行環境を初期状態にリセットしますが、履歴は保持します。 |
| `$wait` | 少なくとも指定されたミリ秒数だけ待機します。 |

Visual Studio 拡張機能で `IInteractiveWindowCommand` を実装およびエクスポートすることで、コマンドを拡張することもできます ([例](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85))。

## <a name="switching-scopes"></a>スコープの切り替え

既定では、プロジェクトの対話型ウィンドウのスコープは、コマンド プロンプトから実行した場合のように、プロジェクトのスタートアップ ファイルです。 スタンドアロン ファイルの場合は、そのファイルがスコープになります。 ただし、対話型ウィンドウの上部にあるドロップダウン メニューを使って、REPL セッション中にいつでもスコープを変更できます。

![対話型ウィンドウのスコープ](media/interactive-scopes.png)

「`import importlib`」と入力するなどしてモジュールをインポートすると、そのモジュール内の他のスコープに切り替えるためのオプションがドロップダウン リストに表示されます。 対話型ウィンドウのメッセージは新しいスコープも示すため、セッション中にどのようにして特定の状態になったかを追跡できます。

スコープで「`dir()`」と入力すると、関数名、クラス、変数など、そのスコープで有効な識別子が表示されます。 たとえば、`import importlib` に続けて `dir()` を使うと、次にように表示されます。

![importlib スコープ内の対話型ウィンドウ](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>

## <a name="send-code-to-interactive-command"></a>対話型コマンドにコードを送信する

対話型ウィンドウ内で直接作業するだけでなく、エディターで、コードを選び、右クリックして、**[Interactive に送信]** を選ぶか、Ctrl + Enter キーを押します。

![[Interactive に送信] メニュー コマンド](media/interactive-send-to.png)

このコマンドは、開発しながらコードをテストするなど、反復的なまたは革新的なコードの開発に役立ちます。 たとえば、対話型ウィンドウにコードの一部を送信し、その出力を表示した後、上方向キーを押してコードをもう一度表示し、変更してから、Ctrl + Enter キーを押して簡単にテストすることができます  (入力の最後に Enter キーを押すと入力内容が実行されますが、入力の途中で Enter キーを押すと改行が挿入されます)。目的のコードができたら、簡単にプロジェクト ファイルにコピーして戻すことができます。

> [!Tip]
> 既定では、Visual Studio は、対話型ウィンドウからコードをエディターに貼り付けるときに、>>> と ... REPL プロンプトを削除します。 この動作は、**[ツール] > [オプション] > [テキスト エディター] > [Python] > [詳細設定]** タブで **[貼り付け時に REPL プロンプトを削除する]** オプションを使用して変更できます。 「[Options - Miscellaneous Options](options.md#miscellaneous-options)」(オプション ∸ その他のオプション) を参照してください。

<!-- After 15.3 is released, you can also press "Undo" after pasting to restore prompts. Press "Undo" a second time to remove the pasted code entirely. -->

コード ファイルをスクラッチ パッドとして使用していると、小さなコードのブロックを一度に送信したい場合がよくあります。 コードを一緒にグループ化するには、`#%%` で始まるコメントを前のセルを終了するセルの先頭に追加して、コードを*コード セル*としてマーク付けします。 コード セルは折りたたむことも展開することもでき、コード セル内で Ctrl + Enter キーを使用することでセル全体を対話型ウィンドウに送信し、次のセルに移動できます。

Visual Studio は `# In[1]:` のようなコメントで始まるコード セルも検出します。これは、Jupyter Notebook を Python ファイルとしてエクスポートするときに取得する形式です。 この検出は、ノートブックを Python ファイルとしてダウンロードし、Visual Studio で開き、Ctrl + Enter キーを使用して各セルを実行することで、[Azure Notebooks](https://notebooks.azure.com/) からノートブックを簡単に実行できるようにします。

![対話型コード セル](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense の動作

コード エディターの IntelliSense がソース コードの分析のみに基づくのとは異なり、対話型ウィンドウに含まれる IntelliSense はライブ オブジェクトに基づきます。 これらの提案は対話型ウィンドウではより正確です。動的に生成されるコードでは特にそうです。 欠点としては、副作用のある関数 (ログ メッセージなど) は、開発エクスペリエンスに影響を与える可能性があります。

それが問題になる場合は、オプションの「[対話型ウィンドウ オプション](options.md#interactive-windows-options)」で説明されているように、**[ツール] > [オプション] > [Python Tools] > [対話型ウィンドウ]** の **[入力候補モード]** グループにある設定を変更します。
