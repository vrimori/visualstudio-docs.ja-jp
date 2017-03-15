---
title: "MSBuild エラー MSB3071 | Microsoft Docs"
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
  - "MSBuild.Exec.AllDriveLettersMappedError"
helpviewer_keywords: 
  - "MSB3071"
ms.assetid: 8afbc6ec-e399-4f06-a30b-f33c87642ef7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3071
**A: から Z: までのすべてのドライブ文字は使用中です。  作業ディレクトリ "\<パス\>" は UNC パスであるため、"Exec" タスクには UNC パスをマップできる使用可能なドライブ文字が必要です。  このコマンドを再度試してみる前に、1 つ以上の共有リソースを切断してドライブ文字を解放するか、ローカルの作業ディレクトリを指定してください。**  
  
 現在、A: から Z: のすべてのドライブ名が使用されています。  指定された作業ディレクトリは UNC パスであるため、`Exec` タスクを使用するには、UNC パスに対応付ける空きドライブ名が必要です。  
  
### このエラーを解決するには  
  
-   共有リソースを少なくとも 1 つ解放し、ドライブ名の空きを作ります。  
  
-   ローカル作業ディレクトリを指定してから、もう一度このコマンドを実行します。  
  
## 参照  
 [Exec Task](../msbuild/exec-task.md)