---
title: "Watch コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.watch"
helpviewer_keywords: 
  - "Debug.Watch コマンド"
  - "Watch コマンド"
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Watch コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定したインスタンスの **\[ウォッチ\]** ウィンドウを作成し、開きます。  **\[ウォッチ\]** ウィンドウを使用すると、変数、式、およびレジスタの値を計算したり、こうした値を編集したりできます。また、結果を保存することもできます。  
  
## 構文  
  
```  
Debug.Watch[index]  
```  
  
## 引数  
 `index`  
 必ず指定します。  ウォッチ ウィンドウのインスタンス番号です。  
  
## 解説  
 `index` は、整数です。  有効な値は、1、2、3、および 4 です。  
  
## 使用例  
  
```  
>Debug.Watch1  
```  
  
## 参照  
 [\[自動変数\] ウィンドウと \[ローカル\] ウィンドウ](../Topic/Autos%20and%20Locals%20Windows.md)   
 [方法 :ウィンドウで値を編集する](../Topic/How%20to:%20Edit%20a%20Value%20in%20a%20Variable%20Window.md)   
 [方法 :ダイアログ ボックスを使用する](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)