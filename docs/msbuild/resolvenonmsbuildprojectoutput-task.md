---
title: "ResolveNonMSBuildProjectOutput Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
helpviewer_keywords: 
  - "MSBuild, ResolveNonMSBuildProjectOutput task"
  - "ResolveNonMSBuildProjectOutput task [MSBuild]"
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# ResolveNonMSBuildProjectOutput Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild 以外のプロジェクト参照に対する出力ファイルを確認します。  
  
## パラメーター  
 `ResolveNonMSBuildProjectOutput` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`PreresolvedProjectOutputs`|省略可能な `String` 型のパラメーターです。<br /><br /> 解決済みのプロジェクト出力を含む XML 文字列を指定します。|  
|`ProjectReferences`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]`  型のパラメーターです。<br /><br /> プロジェクト参照を指定します。|  
|`ResolvedOutputPaths`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> 解決済みの参照パスのリストが含まれます \(また、元のプロジェクト参照属性が保持されます\)。|  
|`UnresolvedProjectReferences`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> 出力の事前解決リストを使用して解決できなかったプロジェクト参照項目のリストが含まれます。<br /><br /> Visual Studio では MSBuild 以外のプロジェクトのみが事前解決されるので、これは、このリストに含まれるプロジェクト参照が MSBuild 形式であることを意味します。|  
  
## 解説  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)