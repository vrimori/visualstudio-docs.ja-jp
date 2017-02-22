---
title: "GoTo コマンド | Microsoft Docs"
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
  - "edit.goto"
helpviewer_keywords: 
  - "Debug.Goto コマンド"
  - "Go To コマンド"
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GoTo コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定した行にカーソルを移動します。  
  
## 構文  
  
```  
Edit.GoTo [linenumber]  
```  
  
## 引数  
 `linenumber`  
 省略可能です。  移動先の行番号を示す整数。  
  
## 解説  
 行番号の開始値は 1 です。  `linenumber` の値が 1 より小さい場合は、最初の行が表示されます。  `linenumber` の値が最後の行番号より大きい場合は、最後の行が表示されます。  
  
 `linenumber` の値を指定しない場合は、**\[指定行へのジャンプ\]** ダイアログ ボックスが表示されます。  
  
 このコマンドのエイリアスは GoToLn です。  
  
## 使用例  
  
```  
>Edit.GoTo 125  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)