---
title: "UnregisterAssembly タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: 21
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 9f2973dcb28338d26b0c3372a95d166d1b2170a0
ms.lasthandoff: 02/22/2017

---
# <a name="unregisterassembly-task"></a>UnregisterAssembly タスク
COM 相互運用のために、指定されたアセンブリの登録を解除します。 [RegisterAssembly タスク](../msbuild/registerassembly-task.md)とは逆の処理になります。  
  
## <a name="parameters"></a>パラメーター  
 `UnregisterAssembly` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`Assemblies`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 登録解除するアセンブリを指定します。|  
|`AssemblyListFile`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> `RegisterAssembly` タスクと `UnregisterAssembly` タスクの間の状態に関する情報が含まれます。 これにより、`RegisterAssembly` タスクで登録に失敗したアセンブリの登録をタスクが解除しないようにできます。<br /><br /> このパラメーターが指定されている場合、`Assemblies` と `TypeLibFiles` のパラメーターは無視されます。|  
|`TypeLibFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> 指定したアセンブリから指定したタイプ アセンブリを登録解除します。 **注:** このパラメーターは、タイプ ライブラリのファイル名がアセンブリ名と異なる場合にのみ必要です。|  
  
## <a name="remarks"></a>コメント  
 アセンブリが存在していなくても、このタスクは正常に終了します。 存在しないアセンブリの登録を解除しようとした場合、タスクは警告を発行して正常終了します。 これは、アセンブリ登録をレジストリから削除することが、このタスクのジョブであるためです。 アセンブリが存在しない場合、アセンブリはレジストリに登録されていないため、タスクは正常に終了します。  
  
 このタスクでは、上記のパラメーター以外に、<xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> クラスからパラメーターを継承し、このクラス自体は <xref:System.MarshalByRefObject> クラスから継承されます。 `MarshalByRefObject` クラスは <xref:Microsoft.Build.Utilities.Task> クラスと同じ機能を提供しますが、独自のアプリケーション ドメインでインスタンス化できます。  
  
## <a name="example"></a>例  
 次の例では `UnregisterAssembly` タスクを使用して、`OutputPath` と `FileName` のプロパティで指定されたパスにあるアセンブリ (存在する場合) を登録解除します。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [RegisterAssembly タスク](../msbuild/registerassembly-task.md)   
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)
