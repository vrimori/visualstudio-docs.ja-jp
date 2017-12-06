---
title: "R Tools for Visual Studio でのデバッグ | Microsoft Docs"
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: cb5128bf6412fa0f06c211f06f0d7f87353d52e0
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2017
---
# <a name="debugging-r-in-visual-studio"></a>Visual Studio での R のデバッグ

R Tools for Visual Studio (RTVS) は、Visual Studio の全デバッグ機能と統合されています (「[Feature Tour of the Visual Studio Debugger](../debugger/debugging-in-visual-studio.md)」(Visual Studio デバッガーの機能ツアー) を参照してください)。 このサポートには、ブレークポイント、実行中のプロセスへのアタッチ、変数の検査と監視、コール スタックの検査が含まれます。 このトピックでは、R および RTVS に固有のデバッグの機能について説明します。

R プロジェクトのスタートアップ R ファイルに対するデバッガーの起動は、他のプロジェクト タイプと同じです。**[デバッグ] > [デバッグ開始]**、F5 キー、またはデバッグ ツールバーの **[Source startup file]\(ソース スタートアップ ファイル\)** を使います。 

![R のデバッガー開始ボタン](media/debugger-start-button.png)

スタートアップ ファイルを変更するには、ソリューション エクスプローラーでファイルを右クリックして、**[R スタートアップ スクリプトとして設定]** を選びます。

いずれの場合も、デバッガーを開始すると、ファイルが対話型ウィンドウに "ソース化" されます。これは、ファイルが読み込まれて、次の対話型ウィンドウの出力のように、そこで実行されることを意味します。

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

この例では、スクリプトのソース指定に `rtvs::debug_source` 関数が使用されています。 RTVS はデバッグの準備でコードを変更する必要があるため、この関数が必要です。 RTVS のソース指定コマンドを使用し、デバッガーをアタッチすると、Visual Studio で `rtvs::debug_source` が自動的に使用されます。

また、対話型ウィンドウから、**[R Tools] > [セッション] > [デバッガーのアタッチ]** コマンド、**[デバッグ] > [R Interactive にアタッチ]** コマンド、またはツールバーの **[デバッガーのアタッチ]** コマンドを使って直接、デバッガーを手動でアタッチすることもできます。 その場合は、ユーザーがデバッグするファイルをソース化する必要があります。 ソース ファイルを手動で指定するには、R で通常の `source` コマンドではなく、`rtvs::debug_source` を使用してください。

デバッガーと対話型ウィンドウの間のこの接続により、異なるパラメーター値での関数の呼び出し (およびデバッグ) のような作業が簡単になります。 たとえば、ソース化されたファイル (つまり、セッションに読み込まれているファイル) に、次のような関数があるものとします。

```R
add <- function(x, y) {
    return(x + y)
}
```

そして、`return` ステートメントにブレークポイントを設定します。 対話型ウィンドウで `add(4,5)` を入力すると、ブレークポイントでデバッガーが停止します。


## <a name="environment-browser-in-the-interactive-window"></a>対話型ウィンドウの環境ブラウザー

デバッガーで停止しているときは、[対話型ウィンドウ](interactive-repl.md)の環境ブラウザー プロンプトでも停止しています。 プロンプトは [`Browse[n]>`] と表示されます。n は数字です。

環境ブラウザーは、いくつかの特別なコマンドをサポートしています。

| コマンド | 説明 | 
| --- | --- |
| n | 次: コード ファイルの次のステートメントを実行します (ステップ オーバーと同じ)。 |
| s | ステップ イン: コード ファイルの次のステートメントを実行し、次のステートメントが関数呼び出しの場合は関数スコープにステップ インします。 | 
| f | 終了: 現在の関数スコープの残りの部分を実行し、呼び出し元に戻ります (ステップ アウトと同じ)。 |
| c、cont | 続行: 次のブレークポイントまでプログラムを実行します。 | 
| Q | 完了: デバッグ セッションを終了します。 |
| where | 履歴を表示: 呼び出し履歴を対話型ウィンドウに表示します。 |
| help | ヘルプを表示: 使用可能なコマンドを対話型ウィンドウに表示します。 |
| &lt;expr&gt; | *expr* の式を評価します。 |

![対話型ウィンドウの環境ブラウザー](media/debugger-environment-browser.png)
