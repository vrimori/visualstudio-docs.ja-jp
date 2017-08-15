---
title: "Move タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 4
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
ms.translationtype: HT
ms.sourcegitcommit: c00adbbabf0d3b82acb17f4a269dfc693246bc69
ms.openlocfilehash: deee8db477425c628e214ad1332884f5a5693ea4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/01/2017

---
# <a name="move-task"></a>Move タスク
ファイルを新しい場所に移動します。  
  
## <a name="parameters"></a>パラメーター  
 `Move` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`DestinationFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> ソース ファイルの移動先ファイルの一覧を指定します。 この一覧は、`SourceFiles` パラメーターに指定された一覧の内容と 1 対 1 で対応している必要があります。 つまり、`SourceFiles` に指定された最初のファイルは、`DestinationFiles` に指定された最初の場所に移動され、2 番目以降のファイルも同様に処理されます。|  
|`DestinationFolder`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> ファイルの移動先ディレクトリを指定します。|  
|`MovedFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> 正常に移動されたアイテムが格納されます。|  
|`OverwriteReadOnlyFiles`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、ファイルが読み取り専用としてマークされている場合でも、ファイルを上書きします。|  
|`SourceFiles`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 移動するファイルを指定します。|  
  
## <a name="remarks"></a>コメント  
 `DestinationFolder` パラメーターか `DestinationFiles` パラメーターのいずれかを指定する必要がありますが、両方は指定できません。 両方を指定した場合、タスクは失敗し、エラーがログに記録されます。  

 `Move` タスクでは、対象ファイルに必要なフォルダーを作成します。

 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は <xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)

