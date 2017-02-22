---
title: "方法 : レジスタ値を編集する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.register.edit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "レジスタの値"
  - "[レジスタ] ウィンドウ, 編集 (レジスタの値を)"
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : レジスタ値を編集する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[レジスタ\] ウィンドウは、**\[オプション\]** ダイアログ ボックス、**\[デバッグ\]** ノードで、アドレスレベルのデバッグが有効になっている場合にのみ、使用できます。  
  
### レジスタ値を変更するには  
  
1.  \[レジスタ\] ウィンドウで、**Tab** キーまたはマウスを使用して、変更する値にカーソルを置きます。  入力するときは、上書きする値の直前の位置にカーソルを置く必要があります。  
  
2.  新しい値を入力します。  
  
    > [!CAUTION]
    >  レジスタ値を変更すると \(特に EIP レジスタと EBP レジスタの場合は\)、プログラムの実行に影響する場合があります。  
  
    > [!CAUTION]
    >  浮動小数点値を編集すると、小数部分の 10 進とバイナリの変換により、多少の誤差が発生する場合があります。  特に影響のないように見える編集でも、浮動小数点レジスタの最下位バイトが変化する場合があります。  
  
## 参照  
 [方法: \[レジスタ\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Registers%20Window.md)