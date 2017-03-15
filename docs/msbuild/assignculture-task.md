---
title: "AssignCulture Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, AssignCulture task"
  - "AssignCulture task [MSBuild]"
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# AssignCulture Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このタスクは、有効な .NET カルチャ ID 文字列をファイル名の一部とするアイテムの一覧を受け取り、対応するカルチャ ID を格納した `Culture` という名前のメタデータを持つアイテムを作成します。  たとえば、ファイル名 Form1.fr\-fr.resx には、"fr\-fr" という ID が埋め込まれています。したがって、このタスクでは、`fr-fr` という値の `Culture` メタデータを持つ、同じファイル名のアイテムが作成されます。  このタスクでは、ファイル名からカルチャ名を削除したファイル名の一覧も作成されます。  
  
## タスク パラメーター  
 `AssignCulture` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`AssignedFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> `Files` パラメーターで受け取ったアイテムの一覧が格納されています。各アイテムには `Culture` メタデータ エントリが追加されています。<br /><br /> `Files` パラメーターで受け取ったアイテムに、既に `Culture` メタデータ エントリが格納されている場合には、この元のメタデータ エントリが使用されます。<br /><br /> このタスクでは、ファイル名に有効なカルチャ ID が含まれている場合にだけ、`Culture` メタデータ エントリが割り当てられます。  カルチャ ID は、ファイル名で、最後の 2 つのドットの間に埋め込まれている必要があります。|  
|`AssignedFilesWithCulture`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> `AssignedFiles` パラメーターに含まれるアイテムのうち、`Culture` メタデータ エントリを持つアイテムのサブセットを格納してあります。|  
|`AssignedFilesWithNoCulture`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> `AssignedFiles` パラメーターに含まれるアイテムのうち、`Culture` メタデータ エントリを持たないアイテムのサブセットが含まれています。|  
|`CultureNeutralAssignedFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> `AssignedFiles` パラメーターに作成されたアイテムの一覧と同じ、アイテムの一覧が含まれていますが、ファイル名からカルチャが削除されています。<br /><br /> この処理では、カルチャ ID が有効な場合にだけ、ファイル名からカルチャが削除されます。|  
|`Files`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> カルチャを割り当てるためのカルチャ名が埋め込まれたファイルの一覧を指定します。|  
  
## 解説  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 使用例  
 `ResourceFiles` アイテム コレクションを指定して `AssignCulture` タスクを実行する例を次に示します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 次の表は、タスクの実行後に出力されるアイテムの値を示しています。  アイテムのメタデータは、アイテムの後にかっこで囲んで示してあります。  
  
|アイテム コレクション|内容|  
|-----------------|--------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` \(メタデータの追加なし\)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` \(メタデータの追加なし\)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`メタデータの追加なし\)|  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)