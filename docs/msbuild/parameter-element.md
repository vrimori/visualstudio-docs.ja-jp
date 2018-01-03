---
title: "Parameter 要素 | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 359f0f58a1c3b813216e4a760a1c750710fb3416
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="parameter-element"></a>Parameter 要素
`UsingTask``TaskFactory` によって生成されるタスクの固有のパラメーターについての情報が格納されます。  要素の名前はパラメーターの名前です。  詳しくは、「[UsingTask 要素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)」をご覧ください。  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  

## <a name="syntax"></a>構文  

```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  

## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  

### <a name="attributes"></a>属性  

|属性|説明|  
|---------------|-----------------|  
|`ParameterType`|省略可能な属性です。<br /><br /> パラメーターの .NET 型です ("System.String" など)。|  
|`Output`|省略可能な Boolean 属性です。<br /><br /> `true` の場合、このパラメーターはタスクの出力パラメーターです。 既定では、値は `false` です。|  
|`Required`|省略可能な Boolean 属性です。<br /><br /> `true` の場合、このパラメーターはタスクの必須パラメーターです。 既定では、値は `false` です。|  

### <a name="child-elements"></a>子要素  
 なし。  

### <a name="parent-elements"></a>親要素  

|要素|説明|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|`UsingTask``TaskFactory` によって生成されるタスクで使用される省略可能なパラメーターのリストが格納されます。|  

## <a name="example"></a>例  
 `Parameter` 要素を使用する方法を次の例に示します。  

```xml  
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

## <a name="see-also"></a>参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)   
 [プロジェクト ファイル スキーマ リファレンス](../msbuild/msbuild-project-file-schema-reference.md)
