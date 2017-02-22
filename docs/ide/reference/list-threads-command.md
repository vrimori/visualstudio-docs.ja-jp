---
title: "ListThreads コマンド | Microsoft Docs"
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
  - "debug.listthreads"
helpviewer_keywords: 
  - "Debug.ListThreads コマンド"
  - "スレッドの一覧表示コマンド"
  - "ListThreads コマンド"
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ListThreads コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

現在のプログラムのスレッド一覧を表示します。  
  
## 構文  
  
```  
Debug.ListThreads [index]  
```  
  
## 引数  
 `index`  
 省略可能です。  スレッドをインデックスで選択して、現在のスレッドにします。  
  
## 解説  
 指定した場合、そのスレッドが引数 `index` により現在のスレッドとしてマークされます。  一覧の現在のスレッドの横にアスタリスク \(\*\) が表示されます。  
  
## 使用例  
  
```  
>Debug.ListThreads   
```  
  
## 参照  
 [ListCallStack コマンド](../../ide/reference/list-call-stack-command.md)   
 [ListDisassembly コマンド](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)