---
title: "AddExistingSolutionItem コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "project.addexistingitem"
helpviewer_keywords: 
  - "既存項目の追加コマンド"
  - "File.AddExistingItem コマンド"
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# AddExistingSolutionItem コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

既存のファイルを現在のソリューションに追加して、そのファイルを開きます。  
  
## 構文  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## 引数  
 `filename`  
 必ず指定します。  現在のソリューションに追加するアイテムの完全パスとファイル名を拡張子を付けて指定します。  ファイルのパスまたはファイル名にスペースが含まれている場合は、パス全体を引用符で囲みます。  
  
## スイッチ  
 \/e: `editorname`  
 省略可能です。  ファイルを開くために使用するエディターの名前を指定します。  引数を指定してあり、エディター名を指定していない場合は、**\[ファイルを開くアプリケーションの選択\]** ダイアログ ボックスが表示されます。  
  
 引数 \/e:`editorname` の構文では、エディター名を **\[ファイルを開くアプリケーションの選択\] ダイアログ ボックス**に表示されたとおりに引用符で囲んで使用します。  たとえば、ソース コード エディターでスタイル シートを開くには、引数 \/e:`editorname` に次のように入力します。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 解説  
 オート コンプリートでは、入力した文字列と一致する正しいパスおよびファイル名が検索されます。  
  
## 使用例  
 ファイル Form1.frm を現在のソリューションに追加するコードは次のとおりです。  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)