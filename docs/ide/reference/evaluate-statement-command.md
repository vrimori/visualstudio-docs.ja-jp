---
title: "Evaluate Statement コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.evaluatestatement"
helpviewer_keywords: 
  - "Debug.EvaluateStatement コマンド"
  - "ステートメントの評価コマンド"
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Evaluate Statement コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定したステートメントを評価し、表示します。  
  
## 構文  
  
```  
Debug.EvaluateStatement text   
```  
  
## 引数  
 `text`  
 必ず指定します。  評価するステートメント。  
  
## 解説  
 **EvaluateStatement** コマンドをどのウィンドウに入力するかによって、等号 \(\=\) を比較演算子として解釈するのか、代入演算子として解釈するのかが決まります。  
  
 **\[コマンド\]** ウィンドウの場合、等号 \(\=\) は、比較演算子と解釈されます。  したがって、たとえば変数 `a` と変数 `b` の値が異なる場合、次のコマンド  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 は、値 `false` を返します。  
  
 一方、**\[イミディエイト\]** ウィンドウの場合、等号 \(\=\) は、代入演算子と解釈されます。  したがって、たとえば次のコマンド  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 では、変数 `a` に変数 `b` の値が代入されます。  
  
## 使用例  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## 参照  
 [Print コマンド](../../ide/reference/print-command.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)