---
title: "R Tools for Visual Studio でのデバッグ | Microsoft Docs"
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb5fe5f8-03bc-42bf-8346-c845036a9c6c
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
ms.openlocfilehash: 01bc916eb656cb8e24279498b7b0236fb8eb0e80
ms.contentlocale: ja-jp
ms.lasthandoff: 05/12/2017

---


# <a name="debugging-r-in-visual-studio"></a>Visual Studio での R のデバッグ

R Tools for Visual Studio (RTVS) は、ブレークポイント、実行中のプロセスへのアタッチ、変数の検査と監視、呼び出し履歴の検査など、Visual Studio のすべてのデバッグ機能 (「[Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)」を参照) と統合します。 このトピックでは、R および RTVS に固有のデバッグの機能について説明します。

R プロジェクトのスタートアップ R ファイルに対するデバッガーの起動は、他のプロジェクト タイプと同じです。**[デバッグ] > [デバッグ開始]**、F5 キー、または次に示すデバッグ ツールバーの **[Source startup file]\(ソース スタートアップ ファイル\)** を使います。 スタートアップ ファイルを変更するには、ソリューション エクスプローラーでファイルを右クリックして、**[R スタートアップ スクリプトとして設定]** を選びます。

![R のデバッガー開始ボタン](media/debugger-start-button.png)

いずれの場合も、デバッガーを開始すると、ファイルが対話型ウィンドウに "ソース化" されます。これは、ファイルが読み込まれて、そこで実行されることを意味します。 実際、デバッグを開始すると、次のような出力が対話型ウィンドウに表示されます。

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

スクリプトをソース化するために、`rtvs::debug_source` 関数が使われていることがわかります。 RTVS はデバッグの準備でコードを変更する必要があるため、このようにする必要があります。 いずれかの RTVS コマンドを使うと (たとえば、ソリューション エクスプローラーでファイルを右クリックして、**[選択したファイルのソース化]** コマンドを実行するなど)、デバッガーがアタッチされている場合は、呼び出しが `rtvs::debug_source` に自動的にリダイレクトされます。

また、対話型ウィンドウから、**[R Tools] > [セッション] > [デバッガーのアタッチ]** コマンド、**[デバッグ] > [R Interactive にアタッチ]** コマンド、またはツールバーの **[デバッガーのアタッチ]** コマンドを使って直接、デバッガーを手動でアタッチすることもできます。 その場合は、ユーザーがデバッグするファイルをソース化する必要があります。 ファイルを手動でソース化する場合は、通常の `source` コマンドではなく `rtvs::debug_source` を R で使う必要があります。*_場合によっては_* source でもうまくいくことがありますが、`rtvs::debug_source` コマンドを使わないと、すべての場合にデバッグが機能することは保証されません。

デバッガーと対話型ウィンドウの間のこの接続により、異なるパラメーター値での関数の呼び出し (およびデバッグ) のような作業が簡単になります。 たとえば、ソース化されたファイル (つまり、セッションに読み込まれているファイル) に、次のような関数があるものとします。

```R
add <- function(x, y) {
    return(x + y)
}
```

そして、`return` ステートメントにブレークポイントを設定します。 それから対話型ウィンドウで「`add(4,5)`」と入力すると、デバッガーがブレークポイントで停止することがわかります。


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

