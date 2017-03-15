---
title: "SetCurrentProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debug.SetCurrentProcess コマンド"
  - "SetCurrentProcess コマンド"
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# SetCurrentProcess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定されたプロセスをデバッガーでアクティブなプロセスとして設定します。  
  
## 構文  
  
```  
Debug.SetCurrentProcess index  
```  
  
## 引数  
 `index`  
 必須。  プロセスのインデックスです。  
  
## 解説  
 デバッグ中には複数のプロセスにアタッチできますが、デバッガーでアクティブになっているプロセスは常に 1 つだけです。  `SetCurrentProcess` コマンドを使用すると、アクティブなプロセスを設定できます。  
  
## 使用例  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)