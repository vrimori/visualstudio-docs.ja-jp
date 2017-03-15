---
title: "SetRadix コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.setradix"
helpviewer_keywords: 
  - "Debug.SetRadix コマンド"
  - "基数の設定コマンド"
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# SetRadix コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

整数値の表示に使用される基数を設定または取得します。  
  
## 構文  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## 引数  
 `10`、`16`、`hex`、`dec` のいずれか  
 省略可能です。  10 進 \(10 または dec\) または 16 進 \(16 または hex\)。  引数を省略すると、現在の基数が返されます。  
  
## 使用例  
 次の例では、整数値を 16 進形式で表示するように環境を設定します。  
  
```  
>Debug.SetRadix hex  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)