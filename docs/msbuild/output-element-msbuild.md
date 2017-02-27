---
title: "Output Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Output"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Output> Element [MSBuild]"
  - "Output Element [MSBuild]"
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Output Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

タスクの出力値をアイテムおよびプロパティに格納します。  
  
## 構文  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|`TaskParameter`|必須の属性です。<br /><br /> タスクの出力パラメーターの名前です。|  
|`PropertyName`|`PropertyName` 属性または `ItemName` 属性のいずれかが必要です。<br /><br /> タスクの出力パラメーター値を受け取るプロパティです。  プロジェクトでは、`$(`*PropertyName*`)` という構文を使用してプロパティを参照できます。  このプロパティ名には、新しいプロパティ名を指定することも、プロジェクトで既に定義されているプロパティ名を指定することもできます。<br /><br /> `ItemName` が使用されている場合、この属性は使用できません。|  
|`ItemName`|`PropertyName` 属性または `ItemName` 属性のいずれかが必要です。<br /><br /> タスクの出力パラメーター値を受け取るアイテムです。  プロジェクトでは、`@(`*ItemName*`)` という構文を使用してアイテムを参照できます。  このアイテム名には、新しいアイテム名を指定することも、プロジェクトに既に定義してあるアイテム名を指定することもできます。<br /><br /> `PropertyName` が使用されている場合、この属性は使用できません。|  
|`Condition`|省略可能な属性です。<br /><br /> 評価する条件です。  詳細については、「[Conditions](../msbuild/msbuild-conditions.md)」を参照してください。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[タスク](../msbuild/task-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクのインスタンスを作成し、実行します。|  
  
## 使用例  
 次のコード例は、`Target` 要素内で実行されている `Csc` タスクを示しています。  タスク パラメーターに渡されるアイテムおよびプロパティは、この例の範囲外で宣言されています。  出力パラメーター `OutputAssembly` からの値は、`FinalAssemblyName` アイテムに格納され、出力パラメーター `BuildSucceeded` からの値は、`BuildWorked` プロパティに格納されます。  詳細については、「[タスク](../msbuild/msbuild-tasks.md)」を参照してください。  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## 参照  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [タスク](../msbuild/msbuild-tasks.md)