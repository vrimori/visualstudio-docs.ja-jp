---
title: "SetCurrentThread コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.setcurrentthread"
helpviewer_keywords: 
  - "Debug.SetCurrentThread コマンド"
  - "現在のスレッドを設定するコマンド"
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# SetCurrentThread コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定したスレッドを現在のスレッドとして設定します。  
  
## 構文  
  
```  
Debug.SetCurrentThread index  
```  
  
## 引数  
 `index`  
 必ず指定します。  インデックスによってスレッドを選択します。  
  
## 使用例  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)