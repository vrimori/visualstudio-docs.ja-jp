---
title: "/Diff | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Diff
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

2 つのファイルを比較します。  特殊な違いは、Visual Studio のウィンドウに表示されます。  
  
## 構文  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],  
[TargetDisplayName]  
```  
  
## 引数  
 `SourceFile`  
 必須です。  比較する最初のファイルの完全パスと名前。  
  
 `TargetFile`  
 必須です。  比較する 2 番目のファイルの完全パスと名前  
  
 `SourceDisplayName`  
 省略可能です。  最初のファイルの表示名。  
  
 `TargetDisplayName`  
 省略可能です。  2 番目のファイルの表示名。