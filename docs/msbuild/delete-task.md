---
title: "Delete Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Delete"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Delete task [MSBuild]"
  - "MSBuild, Delete task"
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Delete Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定されたファイルを削除します。  
  
## パラメーター  
 `Delete` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`DeletedFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> 正常に削除されたファイルが記述されます。|  
|`Files`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 削除対象のファイルを指定します。|  
|`TreatErrorsAsWarnings`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、エラーは警告としてログに記録されます。  既定値は `false` です。|  
  
## 解説  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 使用例  
 `MyApp.pdb` ファイルを削除する例を次に示します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <AppName>MyApp</AppName>  
    </PropertyGroup>  
  
    <Target Name="DeleteFiles">  
        <Delete Files="$(AppName).pdb" />  
    </Target>  
</Project>  
```  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)