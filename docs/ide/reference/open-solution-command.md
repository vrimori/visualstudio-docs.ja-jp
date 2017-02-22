---
title: "OpenSolution コマンド | Microsoft Docs"
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
  - "file.opensolution"
helpviewer_keywords: 
  - "File.OpenSolution コマンド"
  - "ソリューションを開くコマンド"
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# OpenSolution コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

既存のソリューションを開きます。他のソリューションが開いている場合は閉じます。  
  
## 構文  
  
```  
File.OpenSolution filename  
```  
  
## 引数  
 `Filename`  
 必ず指定します。  開くソリューションの完全パスとファイル名。  
  
 引数 `filename` の構文でパスに空白が含まれる場合は、引用符で囲む必要があります。  
  
## 解説  
 オート コンプリート機能により、入力している正しいパスおよびファイルが検索されます。  
  
## 使用例  
 ソリューション Test1.sln を開くコードは次のとおりです。  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)