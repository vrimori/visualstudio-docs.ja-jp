---
title: "AddNewSolutionItem コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "project.addnewitem"
helpviewer_keywords: 
  - "新しい項目の追加コマンド"
  - "File.AddNewItem コマンド"
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# AddNewSolutionItem コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

新規ソリューションのアイテム \(.htm、.css、.txt、フレームセットなど\) を現在のソリューションに追加して、そのソリューションを開きます。  
  
## 構文  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## 引数  
 `filename`  
 省略可能です。  ソリューションに追加するアイテムのパスとファイル名。  
  
## スイッチ  
 \/t: `templatename`  
 省略可能です。  作成するファイルの種類を指定します。  テンプレート名を指定しない場合、既定ではテキスト ファイルが作成されます。  
  
 引数 \/t:`templatename` の構文は、**\[新しい項目の追加\]** ダイアログ ボックスの情報を反映します。  完全なカテゴリ名に続けてファイルの種類を入力します。カテゴリ名とファイルの種類は円記号 \(`\`\) で区切り、文字列全体を引用符で囲む必要があります。  
  
 たとえば、テキスト ファイルを新規作成する場合は、引数 \/t:`templatename` に次の値を代入します。  
  
```  
/t:"General\Style Sheet"  
```  
  
 \/e: `editorname`  
 省略可能です。  ファイルを開くエディターの名前です。  引数を指定してあり、エディター名を指定していない場合は、**\[ファイルを開くアプリケーションの選択\]** ダイアログ ボックスが表示されます。  
  
 引数 \/e:`editorname` の構文では、エディター名を **\[ファイルを開くアプリケーションの選択\] ダイアログ ボックス**に表示されたとおりに引用符で囲んで使用します。  
  
 たとえば、ソース コード エディターでスタイル シートを開くには、引数 \/e:`editorname` に次のように入力します。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 使用例  
 新規ソリューションのアイテム MyHTMLpg を現在のソリューションに追加するコードは次のとおりです。  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)