---
title: "OpenFile コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openfile"
helpviewer_keywords: 
  - "File.OpenFile コマンド"
  - "of コマンド"
  - "ファイルを開くコマンド"
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# OpenFile コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

既存のファイルを開き、エディターを指定できます。  
  
## 構文  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## 引数  
 `filename`  
 必ず指定します。  開くファイルの完全パスまたは部分パス、およびファイル名。  パスに空白が含まれる場合は、引用符で囲む必要があります。  
  
## スイッチ  
 \/e: `editorname`  
 省略可能です。  ファイルを開くために使用するエディターの名前を指定します。  引数を指定してあり、エディター名を指定していない場合は、**\[ファイルを開くアプリケーションの選択\]** ダイアログ ボックスが表示されます。  
  
 \/e:`editorname` の引数の構文は、ダイアログ ボックスで開いているので表示されるように引用符で囲まれているエディターの名前を使用します。  
  
 たとえば、ソース コード エディターでファイルを開くには、引数 \/e:`editorname` に次のように入力します。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 解説  
 パスを入力する場合、オート コンプリート機能によって正しいパス名とファイル名が検索されます。  
  
## 使用例  
 次の例では、スタイル ファイル "Test1.css" をソース コード エディターで開きます。  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [イミディエイト ウィンドウ](../../ide/reference/immediate-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)