---
title: "ListDisassembly コマンド | Microsoft Docs"
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
  - "debug.listdisassembly"
helpviewer_keywords: 
  - "Debug.ListDisassembly コマンド"
  - "逆アセンブリの一覧表示コマンド"
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ListDisassembly コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ プロセスが開始され、エラーの処理方法を指定できるようになります。  
  
## 構文  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## スイッチ  
 各スイッチは、完全な形式か省略形式のいずれかで呼び出すことができます。  
  
 \/count:`number`、\/c:`number`、\/length:`number`、または \/l:`number`  
 省略可能です。  表示する命令の数を指定します。  既定値は 8 です。  
  
 \/endaddress: `expression` または \/e: `expression`  
 省略可能です。  逆アセンブリを停止するアドレスを指定します。  
  
 \/codebytes:`yes`&#124;`no`、\/bytes:`yes`&#124;`no`、または \/b:`yes`&#124;`no`  
 省略可能です。  コード バイトを表示するかどうかを指定します。  既定値は `no`です。  
  
 \/source:`yes`&#124;`no` または \/s:`yes`&#124;`no`  
 省略可能です。  ソース コードを表示するかどうかを指定します。  既定値は `no`です。  
  
 \/symbolnames:`yes`&#124;`no`、\/names:`yes`&#124;`no`、または \/n:`yes`&#124;`no`  
 省略可能です。  シンボル名を表示するかどうかを指定します。  既定値は `yes`です。  
  
 \[\/linenumbers:`yes`&#124;`no`\]  
 省略可能です。  ソース コードに関連付けられている行番号の表示を有効にします。  \/linenumbers スイッチを使用するには、\/source スイッチの値が `yes` である必要があります。  
  
## 使用例  
  
```  
>Debug.ListDisassembly  
```  
  
## 参照  
 [ListCallStack コマンド](../../ide/reference/list-call-stack-command.md)   
 [ListThreads コマンド](../../ide/reference/list-threads-command.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)