---
title: "Print コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.print"
helpviewer_keywords: 
  - "Debug.Print コマンド"
  - "Print コマンド"
  - "Print メソッド"
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Print コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

式を評価するか、指定テキストを表示します。  
  
## 構文  
  
```  
Debug.Print text  
```  
  
## 引数  
 `text`  
 必ず指定します。  評価対象の式または表示対象のテキストです。  
  
## 解説  
 このコマンドのエイリアスとして疑問符 \(?\) を使用できます。  したがって、たとえば次のコマンド  
  
```  
>Debug.Print expA  
```  
  
 は、次のように記述することもできます。  
  
```  
>? expA  
```  
  
 コマンドをどちらで入力した場合でも、式 `expA` の現在の値が返されます。  
  
## 使用例  
  
```  
>Debug.Print varA  
```  
  
## 参照  
 [Evaluate Statement コマンド](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)