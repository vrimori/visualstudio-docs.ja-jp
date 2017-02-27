---
title: "Symbol Path コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.symbolpath"
helpviewer_keywords: 
  - "Debug.SymbolPath コマンド"
  - "シンボル パス コマンド"
  - "SymbolPath コマンド"
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Symbol Path コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッガーによってシンボルが検索されるディレクトリの一覧を設定します。  
  
## 構文  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## 引数  
 `pathname`  
 省略可能。  デバッガーによってシンボルが検索されるパスを、セミコロンで区切った一覧です。  
  
## 解説  
 `pathname` を指定しない場合、シンボル用の現在のパスがコマンドによって一覧表示されます。  
  
## 使用例  
 次の例では、シンボル ディレクトリの一覧に 2 つのパスを追加します。  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## 使用例  
 次の例では、シンボル用の現在のパスをセミコロンで区切った一覧が表示されます。  
  
```  
Debug.SymbolPath  
```  
  
## 参照  
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)