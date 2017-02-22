---
title: "GetFrameworkSdkPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkSdkPath task [MSBuild]"
  - "MSBuild, GetFrameworkSdkPath task"
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetFrameworkSdkPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] へのパスを取得します。  
  
## タスク パラメーター  
 `GetFrameworkSdkPath` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`FrameworkSdkVersion20Path`|省略可能な `String` 型の読み取り専用出力パラメーターです。<br /><br /> .NET SDK Version 2.0 のパスを返します \(存在する場合\)。  それ以外の場合は、`String.Empty` を返します。|  
|`FrameworkSdkVersion35Path`|省略可能な `String` 型の読み取り専用出力パラメーターです。<br /><br /> .NET SDK Version 3.5 のパスを返します \(存在する場合\)。  それ以外の場合は、`String.Empty` を返します。|  
|`FrameworkSdkVersion40Path`|省略可能な `String` 型の読み取り専用出力パラメーターです。<br /><br /> .NET SDK Version 4.0 のパスを返します \(存在する場合\)。  それ以外の場合は、`String.Empty` を返します。|  
|`Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> .NET SDK のいずれかのバージョンが存在する場合、最新の .NET SDK のパスを返します。  それ以外の場合は、`String.Empty` を返します。|  
  
## 解説  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 使用例  
 次の例では、`GetFrameworkSdkPath` タスクを使用して、[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] へのパスを `SdkPath` プロパティに格納しています。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)