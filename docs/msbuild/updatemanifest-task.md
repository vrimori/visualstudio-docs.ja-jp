---
title: UpdateManifest タスク| Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3fc6b89034815f0eb1ee5762e911c42075d115cc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985564"
---
# <a name="updatemanifest-task"></a>UpdateManifest タスク
マニフェスト内の選択したプロパティを更新し、再署名します。  
  
## <a name="parameters"></a>パラメーター  
 `UpdateManifest` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`ApplicationManifest`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> アプリケーション マニフェストを指定します。|  
|`ApplicationPath`|必須の `String` 型のパラメーターです。<br /><br /> アプリケーション マニフェストのパスを指定します。|  
|`InputManifest`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> 更新するマニフェストを指定します。|  
|`OutputManifest`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型の出力パラメーターです。<br /><br /> 更新されたプロパティを含むマニフェストを指定します。|  
  
## <a name="remarks"></a>コメント  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Utilities.Task> クラスからパラメーターを継承します。 これらの追加パラメーターのリストとその説明については、「[Task 基底クラス](../msbuild/task-base-class.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)