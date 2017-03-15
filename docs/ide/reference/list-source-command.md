---
title: "List Source コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Debug.ListSource"
helpviewer_keywords: 
  - "Debug.ListSource コマンド"
  - "ソースの一覧表示コマンド"
  - "ListSource コマンド"
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# List Source コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース コードの指定行が表示されます。  
  
## 構文  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## スイッチ  
 \/Count:`number`  
 省略可能です。  表示する行数を指定します。  
  
 \/Current  
 省略可能です。  現在の行が表示されます。  
  
 \/File:`filename`  
 省略可能です。  表示するファイルのパスです。  ファイル名を指定しない場合、現在のステートメント行のソース コードがコマンドによって表示されます。  
  
 \/Line:`number`  
 省略可能です。  固有の行番号が表示されます。  
  
 \/ShowLineNumbers:`yes|no`  
 省略可能です。  行番号を表示するかどうかを指定します。  
  
## 解説  
  
## 使用例  
 この例では、Form1.vb ファイルのソース コード 4 行目以降に行番号が付いて表示されます。  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)