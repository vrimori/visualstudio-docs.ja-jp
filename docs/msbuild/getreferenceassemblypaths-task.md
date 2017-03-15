---
title: "GetReferenceAssemblyPaths Task | Microsoft Docs"
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
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# GetReferenceAssemblyPaths Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

各種フレームワークの参照アセンブリのパスを返します。  
  
## パラメーター  
 `GetReferenceAssemblyPaths` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`ReferenceAssemblyPaths`|省略可能な `String[]` 型の出力パラメーターです。<br /><br /> `TargetFrameworkMoniker` パラメーターに基づいてパスを返します。  `TargetFrameworkMoniker` が null または空の場合、このパスは `String.Empty` になります。|  
|`FullFrameworkReferenceAssemblyPaths`|省略可能な `String[]` 型の出力パラメーターです。<br /><br /> モニカーのプロファイル部分を考慮せずに、`TargetFrameworkMoniker` パラメーターに基づいてパスを返します。  `TargetFrameworkMoniker` が null または空の場合、このパスは `String.Empty` になります。|  
|`TargetFrameworkMoniker`|省略可能な `String` 型のパラメーターです。<br /><br /> 参照アセンブリのパスに関連付けられているターゲット フレームワーク モニカーを指定します。|  
|`RootPath`|省略可能な `String` 型のパラメーターです。<br /><br /> 参照アセンブリのパスの生成に使用するルート パスを指定します。|  
|`BypassFrameworkInstallChecks`|省略可能な [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) 型のパラメーターです。<br /><br /> `true` の場合、ターゲット フレームワークに応じて特定のランタイム フレームワークがインストールされていることを確認するために、`GetReferenceAssemblyPaths` によって既定で実行される基本チェックを省略します。|  
|`TargetFrameworkMonikerDisplayName`|省略可能な `String` 型の出力パラメーターです。<br /><br /> ターゲット フレームワーク モニカーの表示名を指定します。|  
  
## 解説  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)