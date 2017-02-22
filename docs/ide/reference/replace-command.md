---
title: "Replace コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replace"
helpviewer_keywords: 
  - "Edit.Replace コマンド"
  - "Replace コマンド"
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Replace コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**\[検索と置換\]** ウィンドウの **\[フォルダーを指定して置換\]** タブにあるオプションを使用してファイル内のテキストを置換します。  
  
## 構文  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
```  
  
## 引数  
 `findwhat`  
 必ず指定します。  一致させるテキストです。  
  
 `replacewith`  
 必ず指定します。  一致したテキストと置き換えるテキストです。  
  
## スイッチ  
 \/all または \/a  
 省略可能です。  検索されたすべての文字列を置換します。  
  
 \/case または \/c  
 省略可能です。  引数 `findwhat` に指定したテキストと大文字\/小文字が完全に一致する場合にだけ、一致したと見なされます。  
  
 \/doc または \/d  
 省略可能です。  現在のドキュメントだけを検索します。  使用可能な検索スコープの中から 1 つを指定します \(`/doc`、`/proc`、`/open`、または `/sel`\)。  
  
 \/hidden または \/h  
 省略可能です。  デザイン時のコントロールのメタデータ、アウトライン表示のドキュメントの非表示の領域、折りたたまれているクラスやメソッドなどの折りたたまれて非表示になっている文字列を検索します。  
  
 \/open または \/o  
 省略可能です。  開いているすべてのドキュメントを 1 つのドキュメントであるかのように検索します。  使用可能な検索スコープの中から 1 つを指定します \(`/doc`、`/proc`、`/open`、または `/sel`\)。  
  
 \/options または \/t  
 省略可能です。  現在の検索オプション設定の一覧を表示します。検索は実行しません。  
  
 \/proc または \/p  
 省略可能です。  現在のプロシージャだけを検索します。  使用可能な検索スコープの中から 1 つを指定します \(`/doc`、`/proc`、`/open`、または `/sel`\)。  
  
 \/regex または \/r  
 省略可能です。  `findwhat` 引数内の定義済み特殊文字を、リテラル文字ではなくテキストのパターンを表す表記として使用します。  正規表現文字の完全なリストについては、「[正規表現](../../ide/using-regular-expressions-in-visual-studio.md)」を参照してください。  
  
 \/reset または \/e  
 省略可能です。  検索を実行せずに、検索オプションを既定の設定に戻します。  
  
 \/sel または \/s  
 省略可能です。  現在の選択項目だけを検索します。  使用可能な検索スコープの中から 1 つを指定します \(`/doc`、`/proc`、`/open`、または `/sel`\)。  
  
 \/up または \/u  
 省略可能です。  現在の位置から上方向にファイルを検索します。  既定では、ファイルの現在位置から検索を開始し、下方向に検索されます。  
  
 \/wild または \/l  
 省略可能です。  `findwhat` 引数内の定義済み特殊文字を、文字または文字列を表す表記として使用します。  
  
 \/word または \/w  
 省略可能です。  完全に一致する単語だけを検索します。  
  
## 使用例  
 開いているすべてのドキュメントで `btnSend` を検索し、`btnSubmit` に置換するコードは次のとおりです。  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## 参照  
 [テキストの検索と置換](../../ide/finding-and-replacing-text.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)