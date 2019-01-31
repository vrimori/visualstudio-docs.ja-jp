---
title: Delete タスク | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b36b2c2a4a4d59426b8ccdd258a0a879ba50a1e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982248"
---
# <a name="delete-task"></a>Delete タスク
指定されたファイルを削除します。  
  
## <a name="parameters"></a>パラメーター  
 `Delete` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`DeletedFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> 正常に削除されたファイルを指定します。|  
|`Files`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 削除するファイルを指定します。|  
|`TreatErrorsAsWarnings`|省略可能な `Boolean` 型のパラメーターです<br /><br /> `true` の場合、エラーは警告として記録されます。 既定値は `false` です。|  
  
## <a name="remarks"></a>コメント  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、*MyApp.pdb* ファイルを削除します。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <AppName>MyApp</AppName>  
    </PropertyGroup>  
  
    <Target Name="DeleteFiles">  
        <Delete Files="$(AppName).pdb" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)
