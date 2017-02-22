---
title: "OpenProject コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openproject"
helpviewer_keywords: 
  - "File.OpenProject コマンド"
  - "op コマンド"
  - "プロジェクトを開くコマンド"
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# OpenProject コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

既存のプロジェクトを開きます。  
  
## 構文  
  
```  
File.OpenProject filename  
```  
  
## 引数  
 `filename`  
 必ず指定します。  開くプロジェクトの完全パスとファイル名。  
  
 引数 `filename` の構文でパスに空白が含まれる場合は、引用符で囲む必要があります。  
  
## 解説  
 オート コンプリート機能により、入力している正しいパスおよびファイルが検索されます。  
  
 このコマンドは、デバッグ時には使用できません。  
  
## 使用例  
 Test1 という [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] プロジェクトを開く例を次に示します。  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)