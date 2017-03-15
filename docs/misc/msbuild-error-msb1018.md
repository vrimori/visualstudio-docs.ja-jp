---
title: "MSBuild エラー MSB1018 | Microsoft Docs"
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
  - "MSBuild.InvalidVerbosityError"
helpviewer_keywords: 
  - "MSB1018"
ms.assetid: fb4deacc-a799-44e8-8980-d70d9da4caa1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB1018
**詳細レベルが無効です。**  
  
 無効な詳細出力レベルが指定されています。  
  
### このエラーを解決するには  
  
1.  詳細出力レベルのスペルを確認します。  指定可能な詳細出力のレベルは、q\[uiet\]、m\[inimal\]、n\[ormal\]、d\[etailed\]、diag\[nostic\] です \(`/verbosity:quiet`、 `/verbosity:q`、`/v:q` など\)。  
  
## 参照  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)   
 [ビルド ロガー](../msbuild/build-loggers.md)