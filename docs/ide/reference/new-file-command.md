---
title: "NewFile コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.newfile"
helpviewer_keywords: 
  - "File.NewFile コマンド"
  - "新しいファイルコマンド"
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# NewFile コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

新規ファイルを作成して開きます。  ファイルは \[その他のファイル\] フォルダーの下に表示されます。  
  
## 構文  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## 引数  
 `filename`  
 省略可能です。  ファイルの名前。  名前を指定しない場合は、既定の名前が付けられます。  テンプレート名がない場合は、テキスト ファイルが作成されます。  
  
## スイッチ  
 \/t: `templatename`  
 省略可能です。  作成するファイルの種類を指定します。  
  
 \/t:`templatename` の引数の構文は、新しいファイル ダイアログ ボックスの情報を反映します。  カテゴリ名に続けて円記号 \(`\`\)、およびテンプレート名を入力し、文字列全体を引用符で囲みます。  
  
 たとえば、新規の [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] ソース ファイルを作成する場合は、引数 \/t:`templatename` に次の値を代入します。  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 上の例で、C\+\+ File のテンプレートは **\[新しいファイル\]** ダイアログ ボックスの \[Visual C\+\+\] カテゴリにあります。  
  
 \/e: `editorname`  
 省略可能です。  ファイルを開くために使用するエディターの名前を指定します。  引数を指定してあり、エディター名を指定していない場合は、**\[ファイルを開くアプリケーションの選択\]** ダイアログ ボックスが表示されます。  
  
 \/e:`editorname` の引数の構文は、ダイアログ ボックスで開いているので表示されるように引用符で囲まれているエディターの名前を使用します。  
  
 たとえば、ソース コード エディターでファイルを開くには、引数 \/e:`editorname` に次のように入力します。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 使用例  
 次の例では、Web ページ "test1.htm" を新規作成し、それをソース コード エディターで開きます。  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [イミディエイト ウィンドウ](../../ide/reference/immediate-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)