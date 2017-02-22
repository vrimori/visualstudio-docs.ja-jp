---
title: "FormatVersion Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FormatVersion Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

バージョン番号にリビジョン番号を追加します。  
  
-   ケース \#1: 入力: Version\=\<未定義\>;  Revision\=\<考慮しない\>;   出力: OutputVersion\="1.0.0.0"  
  
-   ケース \#2: 入力: Version\="1.0.0.\*"  Revision\="5"  出力: OutputVersion\="1.0.0.5"  
  
-   ケース \#3: 入力: Version\="1.0.0.0"  Revision\=\<考慮しない\>;  出力: OutputVersion\="1.0.0.0"  
  
## パラメーター  
 `FormatVersion` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`FormatType`|省略可能な `String` 型のパラメーターです。<br /><br /> 書式の種類を指定します。<br /><br /> -   "Version" \= バージョン。<br />-   "Path" \= "." を "\_" に置き換えます。|  
|`OutputVersion`|省略可能な `String` 型の出力パラメーターです。<br /><br /> リビジョン番号を含む出力バージョンを指定します。|  
|`Revision`|省略可能な `Int32` 型のパラメーターです。<br /><br /> バージョンに追加するリビジョンを指定します。|  
|`Version`|省略可能な `String` 型のパラメーターです。<br /><br /> 書式を設定するバージョン番号の文字列を指定します。|  
  
## 解説  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)