---
title: "Find コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.find"
helpviewer_keywords: 
  - "Edit.Find コマンド"
  - "Find コマンド"
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Find コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

検索は **検索と置換** のペインの **フォルダーを指定して検索** のタブにあるオプションを使用してファイル。  
  
## 構文  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## 引数  
 `findwhat`  
 必ず指定します。  一致させるテキストです。  
  
## スイッチ  
 \/case または \/c  
 省略可能です。  引数 `findwhat` に指定したテキストと大文字\/小文字までが完全に一致する場合にだけ、一致したと見なされます。  
  
 \/doc または \/d  
 省略可能です。  現在のドキュメントだけを検索します。  使用可能な検索スコープの中から 1 つを指定します \(`/doc`、`/proc`、`/open`、または `/sel`\)。  
  
 \/markall または \/m  
 省略可能です。  現在のドキュメント内で、検索文字列に一致する候補が見つかった行にグラフィックを配置します。  
  
 \/open または \/o  
 省略可能です。  開いているすべてのドキュメントを 1 つのドキュメントであるかのように検索します。  使用可能な検索スコープの中から 1 つを指定します \(`/doc`、`/proc`、`/open`、または `/sel`\)。  
  
 \/options または \/t  
 省略可能です。  現在の検索オプション設定の一覧を表示します。検索は実行しません。  
  
 \/proc または \/p  
 省略可能です。  現在のプロシージャだけを検索します。  使用可能な検索スコープの中から 1 つを指定します \(`/doc`、`/proc`、`/open`、または `/sel`\)。  
  
 \/reset または \/e  
 省略可能です。  検索を実行せずに、検索オプションを既定の設定に戻します。  
  
 \/sel または \/s  
 省略可能です。  現在の選択項目だけを検索します。  使用可能な検索スコープの中から 1 つを指定します \(`/doc`、`/proc`、`/open`、または `/sel`\)。  
  
 \/up または \/u  
 省略可能です。  現在の位置から上方向にファイルを検索します。  既定では、ファイルの現在位置から検索を開始し、下方向に検索されます。  
  
 \/regex または \/r  
 省略可能です。  `findwhat` 引数内の定義済み特殊文字を、リテラル文字ではなくテキストのパターンを表す表記として使用します。  正規表現文字の完全なリストについては、「[正規表現](../../ide/using-regular-expressions-in-visual-studio.md)」を参照してください。  
  
 \/wild または \/l  
 省略可能です。  `findwhat` 引数内の定義済み特殊文字を、文字または文字列を表す表記として使用します。  
  
 \/word または \/w  
 省略可能です。  完全に一致する単語だけを検索します。  
  
## 使用例  
 次の例では、現在選択されているコード セクションで、"somestring" という語を、大文字と小文字を区別して検索します。  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## 参照  
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)