---
title: "MSBuild エラー MSB3022 | Microsoft Docs"
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
  - "MSBuild.Copy.ExactlyOneTypeOfDestination"
helpviewer_keywords: 
  - "MSB3022"
ms.assetid: 74ebcced-8a56-4502-8fef-43d36c79a640
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3022
**"'\<属性\>'" と "'\<属性\>'" の両方が、入力パラメーターとしてプロジェクト ファイルで指定されました。  いずれか 1 つを選択してください。**  
  
 `Copy` タスクでは、`DestinationFiles` と `DestinationDirectory` のどちらかを指定する必要があります。両方のタスク属性を指定することはできません。  
  
### このエラーを解決するには  
  
-   プロジェクト ファイルの `Copy` タスクには、`DestinationFiles` または `DestinationDirectory` のどちらかを指定します。  
  
## 参照  
 [Copy Task](../msbuild/copy-task.md)   
 [タスク](../msbuild/msbuild-tasks.md)