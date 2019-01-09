---
title: Node.js REPL を使用する
description: Visual Studio では、Node.js ランタイムとやり取りするためのサポートが提供されています
ms.date: 12/04/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: bdb5202f383a0e9145a03dae71e11894555f5e33
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926490"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Node.js の対話型ウィンドウを使用する

Node.js Tools for Visual Studio には、インストールされている Node.js ランタイム用の対話型ウィンドウが含まれます。 このウィンドウを使用すると、JavaScript コードを入力して結果をすぐに見たり、npm コマンドを実行して現在のプロジェクトと対話したりできます。 対話型ウィンドウは、REPL (**R**ead/**E**valuate/**P**rint **L**oop) とも呼ばれます。

## <a name="open-the-interactive-window"></a>対話型ウィンドウを開く

ソリューション エクスプローラーで Node.js プロジェクト ノードを右クリックして、**[Node.js 対話型ウィンドウを開く]** を選択することで、対話型ウィンドウを開くことができます。

![プロジェクトのコンテキスト メニューの Node.js 対話型ウィンドウ](../javascript/media/interactivewindow-open-from-project.png)

Node.js 対話型ウィンドウを開く既定のショートカット キーは、**Ctrl + K、N** です。または、ツール バーから **[表示]** > **[ウィンドウ]** > **[Node.js 対話型ウィンドウ]** を選択して、ウィンドウを開くこともできます。

## <a name="use-the-repl"></a>REPL を使用する

開いたら、コマンドを入力することができます。

![Node.js 対話型ウィンドウ](../javascript/media/interactivewindow.png)

対話型ウィンドウにはいくつかの組み込みコマンドがあり、ユーザー宣言の JavaScript 関数と区別するため、先頭にドット プレフィックスが付いています。 次のコマンドがサポートされています。

**.cls、.clear**: エディター ウィンドウの内容を消去し、履歴と実行コンテキストはそのまま維持します。

**.help**: 指定したコマンドのヘルプが表示されます。または、何も指定しないと、使用可能なすべてのコマンドとキー バインドが表示されます。

**.info**: 現在使用されている Node.js 実行可能ファイルについての情報が表示されます。

**.npm** npm コマンドが実行されます。 ソリューションに複数のプロジェクトが含まれている場合は、`.npm [projectname] <npm arguments>` を使用してターゲット プロジェクトを指定します。

**.reset**: 実行環境を初期状態にリセットし、履歴を保持します。

**.save**: 現在の REPL セッションをファイルに保存します。