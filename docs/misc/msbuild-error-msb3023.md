---
title: "MSBuild エラー MSB3023 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.NeedsDestination"
helpviewer_keywords: 
  - "MSB3023"
ms.assetid: 3505ad1e-d54f-4cb4-a299-ac03684cb391
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3023
**コピー先が指定されていません。  "'\<属性\>'" または "'\<属性\>'" を指定してください。**  
  
 `Copy` タスクには、`DestinationFiles` と `DestinationDirectory` のいずれかのタスク属性を使用して、コピー先を指定する必要があります。  
  
### このエラーを解決するには  
  
-   `Copy` タスクの `DestinationFiles` または `DestinationDirectory` を指定します。  
  
## 参照  
 [Copy Task](../msbuild/copy-task.md)   
 [タスク](../msbuild/msbuild-tasks.md)