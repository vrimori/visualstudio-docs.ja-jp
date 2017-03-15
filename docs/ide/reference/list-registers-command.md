---
title: "List Registers コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listregisters"
helpviewer_keywords: 
  - "Debug.ListRegisters コマンド"
  - "レジスタの一覧表示コマンド"
  - "ListRegisters コマンド"
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# List Registers コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

選択したレジスタの値を表示するほか、表示されるレジスタの一覧を変更できます。  
  
## 構文  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## スイッチ  
 \/Display \[{`register`&#124;`registerGroup`}...\]  
 指定した `register` または `registerGroup` の値が表示されます。  `register` も `registerGroup` も指定していない場合は、レジスタの既定の一覧が表示されます。  スイッチを指定していない場合の動作も同様です。  次に例を示します。  
  
 `Debug.ListRegisters /Display eax`  
  
 上記のコードは、次のコードと同じです。  
  
 `Debug.ListRegisters eax`  
  
 \/List  
 すべてのレジスタ グループが一覧に表示されます。  
  
 \/Watch \[{`register`&#124;`registerGroup`}...\]  
 1 つ以上の `register` 値または `registerGroup` 値が一覧に追加されます。  
  
 \/Unwatch \[{`register`&#124;`registerGroup`}...\]  
 1 つ以上の `register` 値または `registerGroup` 値が一覧から削除されます。  
  
## 解説  
 エイリアス `r` を `Debug.ListRegisters` の代わりに使用できます。  
  
## 使用例  
 この例では、`Debug.ListRegisters` のエイリアス `r` を使用して、レジスタ グループ `Flags` の値を表示します。  
  
```  
r /Display Flags  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [デバッグの基礎 : \[レジスタ\] ウィンドウ](../Topic/Debugging%20Basics:%20Registers%20Window.md)   
 [方法: \[レジスタ\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Registers%20Window.md)