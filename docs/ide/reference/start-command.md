---
title: "Start コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.start"
helpviewer_keywords: 
  - "Debug.Start コマンド"
  - "[開始] コマンド"
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Start コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

スタートアップ プロジェクトのデバッグを開始します。  
  
## 構文  
  
```  
Debug.Start [address]  
```  
  
## 引数  
 `address`  
 省略可能です。  プログラムの実行を中断するアドレス。ソース コードでのブレークポイントに似ています。  この引数は、デバッグ モードでだけ有効です。  
  
## 解説  
 **Start** コマンドを実行すると、指定したアドレスまで RunToCursor 操作が実行されます。  
  
## 使用例  
 次の例では、デバッガーを起動し、発生した例外はすべて無視されます。  
  
```  
>Debug.Start  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)