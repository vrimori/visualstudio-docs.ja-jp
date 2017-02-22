---
title: "LogCommandWindowOutput コマンド | Microsoft Docs"
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
  - "tools.logcommandwindowoutput"
helpviewer_keywords: 
  - "コマンド ウィンドウ出力のログを記録するコマンド"
  - "View.LogCommandWindowOutput コマンド"
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LogCommandWindowOutput コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**\[コマンド\]** ウィンドウの入出力をすべてファイルにコピーします。  
  
## 構文  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## 引数  
 `filename`  
 省略可能です。  ログ ファイルの名前。  既定では、ユーザーのプロファイル フォルダーにファイルが作成されます。  ファイル名が既に存在する場合は、既存ファイルの終端にログが追加されます。  ファイルを指定しない場合は、最後に指定したファイルが使用されます。  以前に使用したファイルがない場合は、既定のログ ファイル cmdline.log が作成されます。  
  
> [!TIP]
>  ログ ファイルの保存先を変更するには、ファイルの完全パスを入力します。パスに空白が含まれる場合は、パスを引用符で囲みます。  
  
## スイッチ  
 \/on  
 省略可能です。  指定したファイルで **\[コマンド\]** ウィンドウのログの作成を開始し、ファイルに新しい情報を追加します。  
  
 \/off  
 省略可能です。  **\[コマンド\]** ウィンドウのログの作成を停止します。  
  
 \/overwrite  
 省略可能です。  引数 `filename` に指定したファイル名が既存のファイルと同じ場合は、既存のファイルが上書きされます。  
  
## 解説  
 ファイルを指定しない場合、既定では、ファイル cmdline.log が作成されます。  既定では、このコマンドのエイリアスは Log です。  
  
## 例  
 新規のログ ファイル cmdlog を作成してコマンドのログ作成を開始するコードは次のとおりです。  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 コマンドのログを停止するコードは次のとおりです。  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 以前のログ ファイルを使用してコマンドのログを再開するコードは次のとおりです。  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)