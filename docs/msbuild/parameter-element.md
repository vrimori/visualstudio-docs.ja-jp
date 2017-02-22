---
title: "Parameter Element | Microsoft Docs"
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
  - "Parameter element [MSBuild]"
  - "<Parameter> element [MSBuild]"
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Parameter Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`UsingTask` `TaskFactory` によって生成されるタスクの固有のパラメーターについての情報が格納されます。要素の名前はパラメーターの名前です。詳細については、「[UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md)」を参照してください。  
  
## 構文  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|`ParameterType`|省略可能な属性です。<br /><br /> パラメーターの .NET 型です \("System.String" など\)。|  
|`Output`|省略可能な Boolean 型の属性です。<br /><br /> `true` の場合、このパラメーターはタスクの出力パラメーターです。  既定では、値は `false` です。|  
|`Required`|省略可能な Boolean 型の属性です。<br /><br /> `true` の場合、このパラメーターはタスクの必須パラメーターです。  既定では、値は `false` です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|`UsingTask` `TaskFactory` によって生成されるタスクで使用される省略可能なパラメーターのリストが格納されます。|  
  
## 使用例  
 `Parameter` 要素を使用する方法を次の例に示します。  
  
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