---
title: AssignTargetPath タスク | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63836579d43ed9415d85f987b04b440eb387e95c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536378"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[AssignTargetPath タスク](https://docs.microsoft.com/visualstudio/msbuild/assigntargetpath-task)します。  
  
  
このタスクはリスト ファイルを受け入れ、`<TargetPath>` 属性がまだ指定されていない場合は、この属性を追加します。  
  
## <a name="task-parameters"></a>タスク パラメーター  
 `AssignTargetPath` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`RootFolder`|省略可能な `string` 型の入力パラメーターです。<br /><br /> ターゲット リンクを格納しているフォルダーのパスが格納されます。|  
|`Files`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 入力パラメーターです。<br /><br /> ファイルの受信リストが格納されます。|  
|`AssignedFiles`|Optional<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]` 出力パラメーターです。<br /><br /> ファイルの結果のリストが格納されます。|  
  
## <a name="remarks"></a>Remarks  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`AssignTargetPath` タスクを実行してプロジェクトを構成しています。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)



