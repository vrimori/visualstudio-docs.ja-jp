---
title: "MSBuild エラー MSB3072 | Microsoft Docs"
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
  - "MSBuild.Exec.MissingCommandError"
helpviewer_keywords: 
  - "MSB3072"
ms.assetid: c8468e1c-d8c7-441c-b274-123ac856f147
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3072
**"Exec" タスクには実行するためのコマンドが必要です。**  
  
 `Exec` タスクには必ず `Command` 属性を指定する必要があります。  
  
### このエラーを解決するには  
  
1.  プロジェクト ファイルで、`Exec` タスクの属性 `Command` を指定します。  
  
## 参照  
 [Exec Task](../msbuild/exec-task.md)   
 [タスク](../msbuild/msbuild-tasks.md)