---
title: "ReplaceinFiles コマンド | Microsoft Docs"
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
  - "edit.replaceinfiles"
helpviewer_keywords: 
  - "Edit.ReplaceInFiles コマンド"
  - "Replace In Files コマンド"
  - "ReplaceInFiles コマンド"
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ReplaceinFiles コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**\[検索と置換\]** ウィンドウの **\[フォルダーを指定して置換\]** タブにあるオプションを使用してファイル内のテキストを置換します。  
  
## 構文  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
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
  
 \/ext: `extensions`  
 省略可能です。  検索するファイルの拡張子を指定します。  
  
 \/keep または \/k  
 省略可能です。  すべての変更済みファイルを開いたままにします。  
  
 \/lookin: `searchpath`  
 省略可能です。  検索するディレクトリを指定します。  パスにスペースが含まれる場合は、パス全体を引用符で囲みます。  
  
 \/options または \/t  
 省略可能です。  現在の検索オプション設定の一覧を表示します。検索は実行しません。  
  
 \/regex または \/r  
 省略可能です。  `findwhat` 引数内の定義済み特殊文字を、リテラル文字ではなくテキストのパターンを表す表記として使用します。  正規表現文字の完全なリストについては、「[正規表現](../../ide/using-regular-expressions-in-visual-studio.md)」を参照してください。  
  
 \/reset または \/e  
 省略可能です。  検索を実行せずに、検索オプションを既定の設定に戻します。  
  
 \/stop  
 省略可能です。  検索中の場合は、その検索を中断します。  `/stop` を指定すると、他の引数はすべて無視されます。  たとえば、現在の置換操作を中断するには、次のように入力します。  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 \/sub または \/s  
 省略可能です。  引数 \/lookin:`searchpath` に指定したディレクトリ内のサブフォルダーを検索します。  
  
 \/text2 または \/2  
 省略可能です。  **\[検索結果 2\]** ウィンドウに置換結果を表示します。  
  
 \/wild または \/l  
 省略可能です。  `findwhat` 引数内の定義済み特殊文字を、文字または文字列を表す表記として使用します。  
  
 \/word または \/w  
 省略可能です。  完全に一致する単語だけを検索します。  
  
## 使用例  
 次のコードでは、"my visual studio projects" フォルダーに含まれるすべての .cls ファイルで `btnCancel` を検索し、それを `btnReset` で置換して、**\[検索結果 2\]** ウィンドウに置換情報を表示します。  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## 参照  
 [テキストの検索と置換](../../ide/finding-and-replacing-text.md)   
 [\[フォルダーを指定して置換\]](../../ide/replace-in-files.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)