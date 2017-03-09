---
title: "MSBuild エラー MSB1016 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.MissingVerbosityError"
helpviewer_keywords: 
  - "MSB1016"
ms.assetid: 967a9757-0513-48ae-bf1d-b1b019993c70
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB1016
**詳細出力レベルの指定**  
  
 **\/verbosity** スイッチには詳細出力レベルを指定する必要があります。  
  
### このエラーを解決するには  
  
1.  詳細出力のレベルは `/verbosity:<level>` の形式で指定します。  指定可能な詳細出力のレベルは、q\[uiet\]、m\[inimal\]、n\[ormal\]、d\[etailed\]、diag\[nostic\] です \(`/verbosity:quiet`、 `/verbosity:q`、`/v:q` など\)。  
  
## 参照  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)