---
title: "AssignTargetPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# AssignTargetPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このタスクはリスト ファイルを受け入れ、`<TargetPath>` 属性がまだ指定されていない場合は、この属性を追加します。  
  
## タスク パラメーター  
 `AssignTargetPath` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|------------|--------|  
|`RootFolder`|省略可能な `string` 型の入力パラメーターです。<br /><br /> ターゲット リンクを格納しているフォルダーのパスが格納されます。|  
|`Files`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の入力パラメーターです。<br /><br /> ファイルの受信リストが格納されます。|  
|`AssignedFiles`|省略可能<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]` 型の出力パラメーターです。<br /><br /> ファイルの結果のリストが格納されます。|  
  
## 解説  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 使用例  
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
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)