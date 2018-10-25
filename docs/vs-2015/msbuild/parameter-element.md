---
title: Parameter 要素 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 632973aab0447ffcd8d2bff5e752683223ea3838
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844485"
---
# <a name="parameter-element"></a>Parameter 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)   
 [プロジェクト ファイル スキーマ リファレンス](../msbuild/msbuild-project-file-schema-reference.md)



