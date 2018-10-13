---
title: XmlPeek タスク | Microsoft Docs
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
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6ad86c061d089b7cedaf040082fe9f51ae26120
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289771"
---
# <a name="xmlpeek-task"></a>XmlPeek タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML ファイルから XPath クエリで指定された値を返します。  
  
## <a name="parameters"></a>パラメーター  
 `XmlPeek` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`Namespaces`|省略可能な `String` 型のパラメーターです。<br /><br /> XPath クエリ プレフィックスの名前空間を指定します。|  
|`Query`|省略可能な `String` 型のパラメーターです。<br /><br /> XPath クエリを指定します。|  
|`Result`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> このタスクによって返される結果が含まれています。|  
|`XmlContent`|省略可能な `String` 型のパラメーターです。<br /><br /> XML 入力を文字列として指定します。|  
|`XmlInputPath`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> XML 入力をファイル パスとして指定します。|  
  
## <a name="remarks"></a>Remarks  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は <xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)



