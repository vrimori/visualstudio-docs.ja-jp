---
title: "CallTarget Task | Microsoft Docs"
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
  - "CallTarget task [MSBuild]"
  - "MSBuild, CallTarget task"
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CallTarget Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロジェクト ファイル内で指定されたターゲットを呼び出します。  
  
## タスク パラメーター  
 `CallTarget` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`RunEachTargetSeparately`|省略可能な `Boolean` 型の出力パラメーターです。<br /><br /> `true` の場合は、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] エンジンがターゲットごとに 1 回呼び出されます。  `false` の場合は、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] エンジンがすべてのターゲットをビルドするために 1 回呼び出されます。  既定値 `false` です。|  
|`TargetOutputs`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> ビルドされたすべてのターゲットの出力がここに格納されます。|  
|`Targets`|省略可能な `String[]` 型のパラメーターです。<br /><br /> ビルドするターゲットを指定します。|  
|`UseResultsCache`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、キャッシュされた結果が返されます \(存在する場合\)。<br /><br /> **メモ** MSBuild タスクが実行された場合、その出力は、ビルド項目のリストとしてスコープ \(\(ProjectFileName, GlobalProperties\)\[TargetNames\]\) にキャッシュされます。|  
  
## 解説  
 `Targets` に指定されたターゲットのビルドが失敗し、`RunEachTargetSeparately` が `true` に設定されている場合は、タスクは残りのターゲットのビルドを継続します。  
  
 既定のターゲットをビルドする場合は、[MSBuild タスク](../msbuild/msbuild-task.md) を使用し、`Projects` パラメーターを `$(MSBuildProjectFile)` と等しくなるように設定します。  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 使用例  
 次の例は、`CallOtherTargets` 内から `TargetA` を呼び出します。  
  
```  
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
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [ターゲット](../msbuild/msbuild-targets.md)