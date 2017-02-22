---
title: "CPPClean Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.cppclean"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), CPPClean task"
  - "CPPClean task (MSBuild (Visual C++))"
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CPPClean Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual C\+\+ プロジェクトのビルド時に MSBuild によって作成される一時ファイルを削除します。  ビルド ファイルを削除するこの処理は、*クリーニング*と呼ばれます。  
  
## パラメーター  
 **CPPClean** タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|**DeletedFiles**|省略可能な `ITaskItem[]` 型の出力パラメーターです。<br /><br /> タスクで使用および生成できる MSBuild 出力ファイル アイテムの配列を定義します。|  
|**DoDelete**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、一時ビルド ファイルを消去します。|  
|**FilePatternsToDeleteOnClean**|必須の `String` 型のパラメーターです。<br /><br /> 消去するファイルの拡張子をセミコロン区切りのリストで指定します。|  
|**FilesExcludedFromClean**|省略可能な `String` 型のパラメーターです。<br /><br /> 消去しないファイルをセミコロン区切りのリストで指定します。|  
|**FoldersToClean**|必須の `String` 型のパラメーターです。<br /><br /> 消去するディレクトリをセミコロン区切りのリストで指定します。  パスは完全パスでも相対パスでもかまいません。また、ワイルドカード記号 \(**\***\) を使用することもできます。|  
  
## 解説  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)