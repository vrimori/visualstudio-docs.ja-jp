---
title: "Warning Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Warning"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Warning task [MSBuild]"
  - "MSBuild, Warning task"
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Warning Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

条件付きステートメントの評価に基づいてビルド中の警告をログに記録します。  
  
## パラメーター  
 `Warning` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`Code`|省略可能な `String` 型のパラメーターです。<br /><br /> 警告に関連付けられた警告コードです。|  
|`File`|省略可能な `String` 型のパラメーターです。<br /><br /> 関連ファイルを指定します \(存在する場合\)。  ファイルを指定しなかった場合は、Warning タスクを含むファイルが使用されます。|  
|`HelpKeyword`|省略可能な `String` 型のパラメーターです。<br /><br /> 警告に関連付けるヘルプ キーワードです。|  
|`Text`|省略可能な `String` 型のパラメーターです。<br /><br /> `Condition` パラメーターが `true` と評価された場合に、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] がログに記録する警告テキストです。|  
  
## 解説  
 `Warning` タスクを使用すると、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトで、次のビルド ステップに進む前に、必要な構成やプロパティがあるかどうかをチェックできます。  
  
 `Warning` タスクの `Condition` パラメーターが `true` と評価された場合、このタスクの `Text` パラメーターの値がログに記録され、ビルド処理が継続されます。  `Condition` パラメーターを指定しない場合は、警告テキストがログに記録されます。  ログ処理の詳細については、「[ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)」を参照してください。  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 使用例  
 次のコード例では、コマンド ラインで設定されるプロパティが設定されているかどうかをチェックします。  プロパティが設定されていない場合、プロジェクトでは警告イベントを発生し、`Warning` タスクの `Text` パラメーターの値がログに記録されます。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## 参照  
 [ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)