---
title: CallTarget タスク | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85ad6261dba80e56ab44f43b4c70df79d63bb509
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001632"
---
# <a name="calltarget-task"></a>CallTarget タスク
プロジェクト ファイル内で指定されたターゲットを呼び出します。  

## <a name="task-parameters"></a>タスク パラメーター  
 `CallTarget` タスクのパラメーターの説明を次の表に示します。  


| パラメーター | 説明 |
|---------------------------| - |
| `RunEachTargetSeparately` | 省略可能な `Boolean` 型の入力パラメーターです。<br /><br /> `true` の場合は、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] エンジンがターゲットごとに 1 回呼び出されます。 `false` の場合は、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] エンジンがすべてのターゲットをビルドするために 1 回呼び出されます。 既定値は `false` です。 |
| `TargetOutputs` | 省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> ビルドされたすべてのターゲットの出力が含まれます。 |
| `Targets` | 省略可能な `String[]` 型のパラメーターです。<br /><br /> ビルドする 1 つまたは複数のターゲットを指定します。 |
| `UseResultsCache` | 省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、キャッシュされた結果が返されます (存在する場合)。<br /><br /> **メモ** MSBuild タスクが実行された場合、その出力は、ビルド項目のリストとしてスコープ ((ProjectFileName, GlobalProperties)[TargetNames]) にキャッシュされます。 |

## <a name="remarks"></a>コメント  
 `Targets` に指定されたターゲットのビルドが失敗し、`RunEachTargetSeparately` が `true` に設定されている場合、タスクは残りのターゲットのビルドを続行します。  

 既定のターゲットをビルドする場合は、[MSBuild タスク](../msbuild/msbuild-task.md)を使用して、`Projects` パラメーターを `$(MSBuildProjectFile)` と等しくなるように設定します。  

 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  

## <a name="example"></a>例  
 次の例では、`CallOtherTargets` 内から `TargetA` を呼び出します。  

```xml  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  

    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  

</Project>  
```  

## <a name="see-also"></a>関連項目  
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)   
 [ターゲット](../msbuild/msbuild-targets.md)