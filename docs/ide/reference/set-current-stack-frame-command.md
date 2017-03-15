---
title: "SetCurrentStackFrame コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.setcurrentstackframe"
helpviewer_keywords: 
  - "Debug.SetCurrentStackFrame コマンド"
  - "現在のスタック フレームを設定するコマンド"
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# SetCurrentStackFrame コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

特定のスタック フレームを設定できます。  
  
## 構文  
  
```  
Debug.SetCurrentStackFrame index  
```  
  
## 引数  
 `index`  
 必ず指定します。  インデックスによってスタック フレームを選択します。  
  
## 使用例  
  
```  
>Debug.SetCurrentStackFrame 1  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)