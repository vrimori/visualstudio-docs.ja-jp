---
title: "QuickWatch コマンド | Microsoft Docs"
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
  - "debug.quickwatch"
helpviewer_keywords: 
  - "Debug.Quickwatch コマンド"
  - "[クイック ウォッチ] コマンド"
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# QuickWatch コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

選択または指定したテキストが [&#91;クイック ウォッチ&#93; ダイアログ ボックス](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)の \[式\] フィールドに表示されます。  このダイアログ ボックスを使用すると、デバッガーで認識された変数や式の現在の値を計算したり、レジスタの内容を調べたりできます。  また、定数ではない変数の値や任意のレジスタの内容を変更することもできます。  
  
## 構文  
  
```  
Debug.QuickWatchq [text]  
```  
  
## 引数  
 `text`  
 省略可能です。  **\[クイック ウォッチ\]** ダイアログ ボックスに追加する文字列です。  
  
## 解説  
 `text` を指定しない場合は、カーソル位置で現在選択されている文字列または単語がウォッチ ウィンドウに追加されます。  
  
## 使用例  
  
```  
>Debug.QuickWatch  
```  
  
## 参照  
 [方法 :ダイアログ ボックスを使用する](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)