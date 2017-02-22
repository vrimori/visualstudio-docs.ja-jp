---
title: "TaskBody Element (MSBuild) | Microsoft Docs"
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
helpviewer_keywords: 
  - "TaskBody element [MSBuild]"
  - "<TaskBody> element [MSBuild]"
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# TaskBody Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`UsingTask` `TaskFactory` に渡されるデータを格納します。詳細については、「[UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md)」を参照してください。  
  
## 構文  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|`Evaluate`|省略可能な Boolean 型の属性です。<br /><br /> `true` の場合、タスクがインスタンス化されるときに、MSBuild によって、情報が `TaskFactory` に渡される前に、内部要素が評価され、項目とプロパティが展開されます。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|Data|`TaskBody` タグで囲まれたテキストが `TaskFactory` にそのまま送信されます。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 内にタスクを登録します。  プロジェクトには 0 個以上の `UsingTask` 要素を設定できます。|  
  
## 使用例  
 次の例は、`TaskBody` 要素を使用し、`Evaluate` 属性を指定する方法を示しています。  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)