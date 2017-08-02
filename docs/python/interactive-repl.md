---
title: "Visual Studio の Python 対話型 REPL | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
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
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: ca444dbe9fea25b205ae2060d462f23957368496
ms.lasthandoff: 04/10/2017

---

# <a name="working-with-the-python-interactive-window"></a>Python 対話型ウィンドウの使用

Visual Studio において各 Python 環境に用意されている対話型の read-evaluate-print loop (REPL) ウィンドウを使うと、コマンド ラインの `python.exe` で実行する REPL が向上します。 対話型ウィンドウ (**[表示] > [その他のウィンドウ] > [&lt;環境&gt; インタラクティブ]** メニュー コマンドで開きます) を使うと、任意の Python コードを入力してすぐに結果を確認できるので、API の学習や実験が容易になり、動作するコードを対話形式で開発してプロジェクトに組み込むことができます。

![Python 対話型ウィンドウ](~/docs/python/media/interactive-window.png)

Visual Studio では、複数の Python REPL モードから選ぶことができます。

| REPL | 説明 | 編集 | デバッグ | イメージ |
| --- | --- | --- | --- | --- |
| 標準 | 既定の REPL、Python と直接対話 | 標準的な編集 (複数行など)。 | はい、`$attach` を使用 | いいえ |
| デバッグ | 既定の REPL、デバッグ対象の Python プロセスと対話 | 標準的な編集 | デバッグのみ | いいえ |
| IPython | REPL は IPython のバックエンドと対話 | IPython コマンド、Pylab の利便性 | いいえ | はい、REPL でインライン |
| IPython (Pylab なし) | REPL は IPython のバックエンドと対話 | 標準的な IPython | いいえ | はい、別のウィンドウ | 

このトピックでは、REPL の**標準**モードと**デバッグ** モードのについて説明します。 IPython モードについて詳しくは、「[Using the IPython REPL](interactive-repl-ipython.md)」(IPython REPL の使用) をご覧ください。

Python 対話型ウィンドウの概要については、「[Getting Started with Python in Visual Studio, Part 5: Interactive REPL](https://youtu.be/yc2CROtTsC0?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)」(Visual Studio での Python の概要、パート 5: 対話型 REPL) (youtube.com、2 分 51 秒) をご覧ください。

> [!VIDEO https://www.youtube.com/embed/yc2CROtTsC0]

## <a name="opening-an-interactive-window"></a>対話型ウィンドウを開く

環境用の対話型ウィンドウを開くにはいくつかの方法があります。

(第 1 の方法) [Python Environments (Python 環境)] ウィンドウに切り替え (**[表示] > [その他のウィンドウ] > [Python Environments (Python 環境)]**、または Ctrl + K、Ctrl + `)、**[Open Interactive Window (対話型ウィンドウを開く)]** コマンドまたは選んだ環境のボタンを選びます。

![Python 環境ウィンドウの対話型ウィンドウへのリンク](~/docs/python/media/interactive-window-opening.png)

(第 2 の方法) **[表示] > [その他のウィンドウ]** には、各環境の**対話型**コマンドがあります。通常は、メニューの下端近くに表示されます。

![[表示] > [その他のウィンドウ] の対話型ウィンドウ メニュー項目](~/docs/python/media/interactive-window-menu.png)

(第 3 の方法) プロジェクトのスタートアップ ファイルで対話型ウィンドウを開くことができます。または、スタンドアロン ファイルの場合は、**[デバッグ] > [Execute [Project | File] in Python Interactive (Python Interactive で [プロジェクト | ファイル] を実行する)]** メニュー コマンドを選びます (Shift + Alt + F5)。

![[Execute Project in Python Interactive (Python Interactive でプロジェクトを実行する)] メニュー](~/docs/python/media/interactive-execute-project.png)

(第 4 の方法) ファイルでコードを選び、後で説明する [Interactive にコードを送信するコマンド](#send-code-to-interactive-command)を使います。

## <a name="interactive-window-options"></a>対話型ウィンドウのオプション

[Python Environments (Python 環境)] ウィンドウの **[Configure interactive window (対話型ウィンドウの構成)]** または **[ツール] > [オプション] > [Python Tools] > [インタラクティブな Windows]** を使って、対話型ウィンドウのさまざまな部分を制御できます。

![Python Interactive ウィンドウのオプション](media/interactive-window-options.png)

**[Debug Interactive Window (デバッグ対話型ウィンドウ)]** のオプション セットも別にあることに注意してください。これらのオプションは、デバッグ セッションの間に使うときに動作を制御します。

![Python Interactive ウィンドウのデバッグ オプション](media/interactive-window-debug-options.png)

## <a name="using-the-interactive-window"></a>対話型ウィンドウの使用

対話型ウィンドウを開いた後は、`>>>` プロンプトで 1 行ずつコードの入力を開始できます。 対話型ウィンドウは、入力と同時に各行を実行します。これには、モジュールのインポートや、変数の定義などが含まれます。 次の図の最初の 2 行にこのことが示されています。

![Python 対話型ウィンドウ](~/docs/python/media/interactive-window.png)

例外はステートメントがコロンで終わる場合で、上の `for` ステートメントと同様に、対話型ウィンドウはコード ブロックを正しく実行するには追加のコード行が必要であることを認識しています。 この場合、行プロンプトが `...` に変わり、ブロックの追加行を入力する必要があることを示します (上の図の 4 番目と 5 番目の行を参照)。 空白行で Enter キーを押すと、対話型ウィンドウはブロックを終了し、インタープリターでブロックを実行します。

> [!Tip]
> 対話型ウィンドウは、囲むスコープに属しているステートメントを自動的にインデントすることにより、Python の通常のコマンドライン REPL エクスペリエンスを向上させます。 対話型ウィンドウの履歴 (上方向キーで再呼び出しされます) は複数行の項目も提供しますが、コマンドライン REPL は単一行しか提供しません。

対話型ウィンドウは、新しいライブラリを試してみるのに優れた方法です。 ライブラリをインポートしたり、サブ パッケージ、クラス、および関数を調べたりすることができます。  Python は、その `help()` 関数によってこのすべての情報を通知します。  また、Visual Studio での Python のサポートでは、エディターで使用されるコードのモデル化に基づいて提案やドキュメントが提供されます。その際、ライブラリを実行する必要はありません。  コードを実行するとき、Visual Studio は Python ランタイムからの情報を使用してこれらの提案を改善します。  

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

コマンドは、MEF (Managed Extensibility Framework for .NET) で拡張することもできます。

## <a name="switching-scopes"></a>スコープの切り替え

既定では、プロジェクトの対話型ウィンドウのスコープは、コマンド プロンプトから実行した場合のように、プロジェクトのスタートアップ ファイルです。 スタンドアロン ファイルの場合は、そのファイルがスコープになります。 ただし、対話型ウィンドウの上部にあるドロップダウン メニューを使って、REPL セッション中にいつでもスコープを変更できます。

![対話型ウィンドウのスコープ](~/docs/python/media/interactive-scopes.png)

「`import os`」と入力するなどしてモジュールをインポートすると、そのモジュール内の他のスコープに切り替えるためのオプションがドロップダウン リストに表示されます。 また、新しいスコープを示すメッセージも対話型ウィンドウに表示され、セッション中にどのようにして特定の状態になったかを監視できます。

スコープで「`dir()`」と入力すると、関数名、クラス、変数など、そのスコープで有効な識別子が表示されます。 たとえば、`$mod importlib` に続けて `dir()` を使うと、次にように表示されます。

![importlib スコープ内の対話型ウィンドウ](~/docs/python/media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>
## <a name="send-code-to-interactive-command"></a>対話型コマンドにコードを送信する

対話型ウィンドウ内で直接作業するだけでなく、エディターで、コードを選び、右クリックして、**[Interactive に送信]** を選ぶことができます。

![[Interactive に送信] メニュー コマンド](~/docs/python/media/interactive-send-to.png)

これは、開発しながらコードをテストするなど、反復的なまたは革新的なコードの開発に役立ちます。 たとえば、対話型ウィンドウにコードの一部を送信し、その出力を表示した後、上方向キーを押してコードをもう一度表示し、変更してから、Ctrl + Enter キーを押して簡単にテストすることができます  (入力の最後に Enter キーを押すと入力内容が実行されますが、入力の途中で Enter キーを押すと改行が挿入されます)。目的のコードができたら、簡単にプロジェクト ファイルにコピーして戻すことができます。

また、コードを選び、右クリックして、**[Send to Defining Module (定義するモジュールに送信)]** を選ぶと、対話型プロセスを検索して、現在編集中のファイルに一致するモジュールを見つけることもできます。 このコマンドは、適切なモジュールが見つかると、`$mod` メタコマンドを使ってそのモジュールに切り替え (対話型ウィンドウのセッション履歴の一部になります)、評価のために選択範囲を対話型ウィンドウに貼り付けます。 このようにすると、エディターにコードをコピーし、対話型ウィンドウでスコープを切り替えて、手動で貼り付ける処理を省略できます。

## <a name="intellisense-behavior"></a>IntelliSense の動作

コード エディターの IntelliSense がソース コードの分析のみに基づくのとは異なり、対話型ウィンドウに含まれる IntelliSense はライブ オブジェクトに基づきます。 これにより、対話型ウィンドウでの候補の方が正確であり、動的に生成されるコードでは特にそうです。 欠点としては、副作用のある関数 (ログ メッセージなど) は、開発エクスペリエンスに影響を与える可能性があります。

それが問題になる場合は、**[ツール] > [オプション] > [Python Tools] > [インタラクティブな Windows]** の **[Completion Mode (完了モード)]** グループにある設定を変更します。

- **[Never evaluate expressions (式を評価しない)]**: 通常の IntelliSense エンジンを修正候補に使います。
- **[Never evaluate expressions containing calls (呼び出しを含む式を評価しない)]**: (既定値) `a.b` などの単純な式は評価されますが、`a().b` などには通常のエンジンが使われます。
- **[Always evaluate expressions (常に式を評価する)]**: 副作用があるかどうかに関係なく、完全な式を実行して修正候補を取得します。
