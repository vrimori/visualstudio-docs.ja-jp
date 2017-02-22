---
title: "ToggleBreakpoint コマンド | Microsoft Docs"
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
  - "debug.togglebreakpoint"
helpviewer_keywords: 
  - "Debug.ToggleBreakPoint コマンド"
  - "ブレークポイントの設定/解除コマンド"
  - "ToggleBreakpoint コマンド"
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ToggleBreakpoint コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ファイル内の現在位置で、現在の状態に基づいてブレークポイントのオン\/オフを切り替えます。  
  
## 構文  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## 引数  
 `text`  
 省略可能です。  指定した場合は、名前付きブレークポイントとして行がマークされます。  それ以外の場合は、名前のないブレークポイントとして行がマークされます。これは **F9** キーを押したときの動作に類似します。  
  
## 使用例  
 次の例は現在のブレークポイントを切り替えます。  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)