---
title: RequiresFramework35SP1Assembly タスク | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5297d1a573542fecc55fa90983befa43df8f3f3d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155367"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly タスク
アプリケーションで .NET Framework 3.5 SP1 が必要であるかどうかを確認します。  
  
## <a name="parameters"></a>パラメーター  
 `RequiresFramework35SP1Assembly` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`Assemblies`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> アプリケーションで参照されるアセンブリを指定します。|  
|`CreateDesktopShortcut`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、インストール中にデスクトップにショートカット アイコンを作成します。|  
|`DeploymentManifestEntryPoint`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> アプリケーションのマニフェスト ファイル名を指定します。|  
|`EntryPoint`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> アプリケーションの実行時に実行する必要があるアセンブリを指定します。|  
|`ErrorReportUrl`|省略可能な `String` 型のパラメーターです。<br /><br /> ClickOnce のインストール時にダイアログ ボックスに表示される Web サイトを指定します。|  
|`Files`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> アプリケーションの公開時に展開されるファイルの一覧を指定します。|  
|`ReferencedAssemblies`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> プロジェクトで参照されるアセンブリを指定します。|  
|`RequiresMinimumFramework35SP1`|省略可能な `Boolean` 型の出力パラメーターです。<br /><br /> `true` の場合、アプリケーションで .NET Framework 3.5 SP1 が必要になります。|  
|`SigningManifests`|省略可能な `Boolean` 型の出力パラメーターです。<br /><br /> `true` の場合、ClickOnce マニフェストが署名されます。|  
|`SuiteName`|省略可能な `String` 型のパラメーターです。<br /><br /> アプリケーションがインストールされ、**[スタート]** メニューに表示されるフォルダーの名前を指定します。|  
|`TargetFrameworkVersion`|省略可能な `String` 型のパラメーターです。<br /><br /> このアプリケーションが対象とする .NET Framework のバージョンを指定します。|  
  
## <a name="remarks"></a>コメント  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は <xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)