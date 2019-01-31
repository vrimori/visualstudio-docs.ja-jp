---
title: TaskBody 要素 (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c95761dd87d9d8d36aaff228d6395547bc07fe41
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015707"
---
# <a name="taskbody-element-msbuild"></a>TaskBody 要素 (MSBuild)
`UsingTask` `TaskFactory` に渡されるデータを含みます。 詳細については、「[UsingTask 要素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)」を参照してください。  

 \<Project>  
 \<UsingTask>  
 \<TaskBody>  

## <a name="syntax"></a>構文  

```xml
<TaskBody Evaluate="true/false" />  
```  

## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  

### <a name="attributes"></a>属性  

|属性|説明|  
|---------------|-----------------|  
|`Evaluate`|省略可能な Boolean 属性です。<br /><br /> `true` の場合、MSBuild は内部要素をすべて評価し、タスクがインスタンス化されるときに項目とプロパティを展開してから情報を `TaskFactory` に渡します。|  

### <a name="child-elements"></a>子要素  

|要素|説明|  
|-------------|-----------------|  
|データ|`TaskBody` タグ間のテキストは `TaskFactory` にそのまま送信されます。|  

### <a name="parent-elements"></a>親要素  

| 要素 | 説明 |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] にタスクを登録する方法を提供します。 1 つのプロジェクトに 0 個以上の `UsingTask` 要素を含めることができます。 |

## <a name="example"></a>例  
 次の例では、`Evaluate` 属性で `TaskBody` 要素を使用する方法を示します。  

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

## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)   
 [プロジェクト ファイル スキーマ リファレンス](../msbuild/msbuild-project-file-schema-reference.md)
