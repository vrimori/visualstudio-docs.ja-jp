---
title: FindAppConfigFile タスク | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bfc2cb26e01552cf056f08ac6b32ba851aff7b3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800368"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
指定したリスト内で app.config ファイルを検索します。  
  
## <a name="parameters"></a>パラメーター  
 `FindAppConfigFile` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`AppConfigFile`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> 存在する場合、リスト内で最初に見つかった一致する項目を指定します。|  
|`PrimaryList`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 第一に検索する一覧を指定します。|  
|`SecondaryList`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 第二に検索する一覧を指定します。|  
|`TargetPath`|必須の `String` 型のパラメーターです。<br /><br /> メタデータとして追加する値を指定します。|  
  
## <a name="remarks"></a>コメント  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は <xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="see-also"></a>「  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)
