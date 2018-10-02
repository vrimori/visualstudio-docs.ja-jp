---
title: ConvertToAbsolutePath タスク | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ConvertToAbsolutePath task [MSBuild]
- MSBuild, ConvertToAbsolutePath task
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8438fcbbfffea57d3238b6a81b2cfa9e11118653
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535067"
---
# <a name="converttoabsolutepath-task"></a>ConvertToAbsolutePath タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ConvertToAbsolutePath Task](https://docs.microsoft.com/visualstudio/msbuild/converttoabsolutepath-task)します。  
  
  
相対パス (参照) を絶対パスに変換します。  
  
## <a name="task-parameters"></a>タスク パラメーター  
 `ConvertToAbsolutePath` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`Paths`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 絶対パスに変換する相対パスの一覧。|  
|`AbsolutePaths`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> 渡された項目の絶対パスの一覧。|  
  
## <a name="remarks"></a>Remarks  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)



