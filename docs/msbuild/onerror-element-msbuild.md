---
title: "OnError Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#OnError"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "OnError Element [MSBuild]"
  - "<OnError Element [MSBuild]"
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# OnError Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

失敗したタスクに対して `ContinueOnError` 属性が `false` である場合に、1 つまたは複数のターゲットを実行します。  
  
## 構文  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`Condition`|省略可能な属性です。<br /><br /> 評価する条件です。  詳細については、「[Conditions](../msbuild/msbuild-conditions.md)」を参照してください。|  
|`ExecuteTargets`|必須の属性です。<br /><br /> タスクが失敗した場合に実行するターゲットです。  複数のターゲットを指定する場合、セミコロン \(;\) で区切ります。  ターゲットは指定した順に実行されます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[Target](../msbuild/target-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクのコンテナー要素です。|  
  
## 解説  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は `Target` 作業の要素の1つが `ErrorAndStop` 失敗した場合 `OnError` の要素を実装します \(または `false`に\)、`ContinueOnError` の属性で。  タスクが失敗した場合は、`ExecuteTargets` 属性に指定したターゲットが実行されます。  ターゲットに `OnError` 要素が複数存在するときにタスクが失敗した場合は、`OnError` の要素が順に実行されます。  
  
 `ContinueOnError` の属性については、[Task Element \(MSBuild\)](../msbuild/task-element-msbuild.md)を参照してください。  ターゲットについては、[ターゲット](../msbuild/msbuild-targets.md)を参照してください。  
  
## 使用例  
 `TaskOne` タスクおよび `TaskTwo` タスクを実行するコードを次に示します。  `TaskOne` が失敗すると、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は `OnError` 要素を評価して、`OtherTarget` ターゲットを実行します。  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## 参照  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [ターゲット](../msbuild/msbuild-targets.md)