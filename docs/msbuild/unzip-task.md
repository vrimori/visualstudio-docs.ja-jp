---
title: Unzip タスク | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 883595eb6cd7565250de216bcae23eba86bf5074
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937024"
---
# <a name="unzip-task"></a>Unzip タスク
指定した場所に *.zip* アーカイブを解凍します。

>[!NOTE]
>`Unzip` タスクは MSBuild 15.8 以降でのみ使用できます。
  
## <a name="parameters"></a>パラメーター  
 `Unzip` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`DestinationFolder`|必須の <xref:Microsoft.Build.Framework.ITaskItem> パラメーター<br /><br /> ファイルの解凍先のフォルダーを指定します。|
|`OverwriteReadOnlyFiles`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、読み取り専用ファイルが上書きされます。 既定値は `false` です。|
|`SkipUnchangedFiles`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、変更されていないファイルの解凍がスキップされます。 既定値は `true` です。 `Unzip` タスクでは、ファイルのサイズが等しく、最終更新時刻が等しい場合、ファイルは変更されていないと見なされます。|
|`SourceFiles`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 解凍する、1 つまたは複数のファイルを指定します。 複数のファイルを指定すると、同じフォルダーに整理されて解凍されます。|
  
## <a name="remarks"></a>コメント  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、アーカイブを解凍し、任意の読み取り専用ファイルを上書きします。
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)
