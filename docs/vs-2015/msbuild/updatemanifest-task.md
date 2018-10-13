---
title: UpdateManifest タスク| Microsoft Docs
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
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43286352ddeb4e2fb3610c5f0b7b67190b526f81
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245493"
---
# <a name="updatemanifest-task"></a>UpdateManifest タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
マニフェスト内の選択したプロパティを更新し、再署名します。  
  
## <a name="parameters"></a>パラメーター  
 `UpdateManifest` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`ApplicationManifest`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> アプリケーション マニフェストを指定します。|  
|`ApplicationPath`|必須の `String` 型のパラメーターです。<br /><br /> アプリケーション マニフェストのパスを指定します。|  
|`InputManifest`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> 更新するマニフェストを指定します。|  
|`OutputManifest`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型の出力パラメーターです。<br /><br /> 更新されたプロパティを含むマニフェストを指定します。|  
  
## <a name="remarks"></a>Remarks  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Utilities.Task> クラスからパラメーターを継承します。 これらの追加パラメーターのリストとその説明については、「[Task Base Class](../msbuild/task-base-class.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)



