---
title: "[検索] ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findcommandbox"
helpviewer_keywords: 
  - "[検索/コマンド] ボックス"
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# [検索] ボックス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[検索\]** ボックスでは、テキストを検索し、Visual Studio コマンドを検索できます。  **\[検索\]** ボックスは、ツール バー コントロールとして使用できますが、既定では表示されません。  **\[標準\]** ツール バーの **\[ボタンの追加または削除\]** を選択し、**\[検索\]** を選択すると、**\[検索\]** ボックスを表示できます。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コマンドを実行するには、コマンドの先頭に不等号 \(\>\) を付けます。  
  
 **Find\/Command** ボックスでは、最近入力した 20 個のアイテムが記憶され、ドロップダウン リストに表示されます。  方向キーを選択すると、一覧を参照できます。  
  
 ![&#91;検索&#93; ボックス](~/docs/ide/media/findcommandbox.png "FindCommandBox")  
\[検索\] ボックス  
  
## テキストの検索  
 既定では、**\[検索\]** ボックスにテキストを指定して Enter キーを押すと、Visual Studio によって、**\[フォルダーを指定して検索\]** ダイアログ ボックスで指定したオプションが使用され、現在のドキュメント ウィンドまたはとツール ウィンドウで検索が行われます。  詳細については、「[テキストの検索と置換](../ide/finding-and-replacing-text.md)」を参照してください。  
  
## コマンドの入力  
 **\[検索\]** ボックスを使用して、文字列の検索ではなく、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の単一のコマンドまたはエイリアスを実行するには、先頭に不等号 \(\>\) を付けて [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コマンドを入力します。  次のように記述します。  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 または、コマンド ウィンドウを使って、単一または複数のコマンドを入力して実行することもできます。  コマンドまたはエイリアスには、単独で入力して実行できるものと、構文に引数の指定が必要なものがあります。  引数を持つコマンドの一覧については、「[Visual Studio コマンド](../ide/reference/visual-studio-commands.md)」を参照してください。  
  
## エスケープ文字  
 コマンド ラインにカレット \(^\) 文字があると、その直後の文字は制御文字としてではなくリテラル文字として解釈されます。  したがって、引用符 \("\)、スペース、先頭のスラッシュ、カレット、その他の任意のリテラル文字をパラメーターまたはスイッチの値に直接埋め込むことができます。ただし、スイッチ名には埋め込むことができません。  次に例を示します。  
  
```  
>Edit.Find ^^t /regex  
```  
  
 カレットは、引用符の前後のどちらに置かれた場合でも同じ働きをします。  行の最後の文字がカレットの場合は無視されます。  
  
## 参照  
 [コマンド ウィンドウ](../ide/reference/command-window.md)   
 [テキストの検索と置換](../ide/finding-and-replacing-text.md)