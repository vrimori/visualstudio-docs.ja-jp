---
title: "[検索/コマンド] ボックス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.findcommandbox
helpviewer_keywords: Find/Command box
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8fa54e65ed581d547d7e4a0c6c5d1c1e0908c0ca
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2017
---
# <a name="findcommand-box"></a>[検索/コマンド] ボックス

**[検索]** ボックスでは、テキストを検索し、Visual Studio コマンドを検索できます。 **[検索]** ボックスは、ツール バー コントロールとして使用できますが、既定では表示されません。 **[標準]** ツール バーの **[ボタンの追加または削除]** を選択し、**[検索]** を選択すると、**[検索]** ボックスを表示できます。

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コマンドを実行するには、コマンドの先頭に不等号 (&gt;) を付けます。

**[検索]** ボックスでは、最近入力した 20 個のアイテムが記憶され、ドロップダウン リストに表示されます。 方向キーを選択すると、一覧を参照できます。

![[検索] ボックス](../ide/media/findcommandbox.png "FindCommandBox")

## <a name="searching-for-text"></a>テキストの検索

既定では、**[検索]** ボックスにテキストを指定して **Enter** キーを押すと、Visual Studio によって、**[フォルダーを指定して検索]** ダイアログ ボックスで指定したオプションが使用され、現在のドキュメント ウィンドウまたはツール ウィンドウで検索されます。 詳細については、「[テキストの検索と置換](../ide/finding-and-replacing-text.md)」を参照してください。

## <a name="entering-commands"></a>コマンドの入力

**[検索]** ボックスを使用して、文字列の検索ではなく、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の単一のコマンドまたはエイリアスを実行するには、コマンドの先頭に不等号 (>) を付けます。 例:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

または、コマンド ウィンドウを使って、単一または複数のコマンドを入力して実行することもできます。 コマンドまたはエイリアスには、単独で入力して実行できるものと、構文に引数の指定が必要なものがあります。 引数を持つコマンドの一覧については、「[Visual Studio コマンド](../ide/reference/visual-studio-commands.md)」をご覧ください。

## <a name="escape-characters"></a>エスケープ文字

コマンドにカレット (^) 文字があると、その直後の文字は制御文字としてではなくリテラル文字として解釈されます。 したがって、引用符 (")、スペース、先頭のスラッシュ、カレット、その他の任意のリテラル文字をパラメーターまたはスイッチの値に直接埋め込むことができます。ただし、スイッチ名には埋め込むことができません。 例:

```
>Edit.Find ^^t /regex
```

カレットは、引用符の前後のどちらに置かれた場合でも同じ働きをします。 行の最後の文字がカレットの場合は無視されます。

## <a name="see-also"></a>関連項目

[コマンド ウィンドウ](../ide/reference/command-window.md)  
[テキストの検索と置換](../ide/finding-and-replacing-text.md)