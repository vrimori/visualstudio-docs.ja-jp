---
title: "GetFrameworkPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkPath task [MSBuild]"
  - "MSBuild, GetFrameworkPath task"
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetFrameworkPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] アセンブリへのパスを取得します。  
  
## タスク パラメーター  
 `GetFrameworkPath` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`FrameworkVersion11Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> Framework Version 1.1 のアセンブリのパスが格納されます \(存在する場合\)。  それ以外の場合は、`null` を返します。|  
|`FrameworkVersion20Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> Framework Version 2.0 のアセンブリのパスが格納されます \(存在する場合\)。  それ以外の場合は、`null` を返します。|  
|`FrameworkVersion30Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> Framework Version 3.0 のアセンブリのパスが格納されます \(存在する場合\)。  それ以外の場合は、`null` を返します。|  
|`FrameworkVersion35Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> Framework Version 3.5 のアセンブリのパスが格納されます \(存在する場合\)。  それ以外の場合は、`null` を返します。|  
|`FrameworkVersion40Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> Framework Version 4.0 のアセンブリのパスが格納されます \(存在する場合\)。  それ以外の場合は、`null` を返します。|  
|`Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> Framework のアセンブリが存在する場合、最新のアセンブリのパスが格納されます。  それ以外の場合は、`null` を返します。|  
  
## 解説  
 複数のバージョンの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] がインストールされている場合には、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] を実行するよう設計されているバージョンが返されます。  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 使用例  
 次の例では、`GetFrameworkPath` タスクを使用して、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] へのパスを `FrameworkPath` プロパティに格納しています。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)