---
title: "Error Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Error"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Error task [MSBuild]"
  - "MSBuild, Error task"
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Error Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

条件付きステートメントの評価に基づいてビルドを停止し、エラーをログに記録します。  
  
## パラメーター  
 `Error` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`Code`|省略可能な `String` 型のパラメーターです。<br /><br /> エラーに関連付けるエラー コードです。|  
|`File`|省略可能な `String` 型のパラメーターです。<br /><br /> エラーを格納するファイルの名前です。  ファイル名を指定しなかった場合は、Error タスクを含むファイルが使用されます。|  
|`HelpKeyword`|省略可能な `String` 型のパラメーターです。<br /><br /> エラーに関連付けるヘルプ キーワードです。|  
|`Text`|省略可能な `String` 型のパラメーターです。<br /><br /> `Condition` パラメーターが `true` と評価された場合に、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] がログに記録するエラー テキストです。|  
  
## 解説  
 `Error` タスクは、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトでロガーに対してメッセージ テキストを発行し、ビルドの実行を中断します。  
  
 `Condition` パラメーターが `true` と評価されると、ビルドを中止し、ログにエラーを記録します。  `Condition` パラメーターが存在しない場合には、その場でエラーを記録し、ビルドを中止します。  ログ処理の詳細については、「[ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)」を参照してください。  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 使用例  
 次のコード例は、必ず指定する必要があるすべてのプロパティが設定されていることを検証します。  プロパティが設定されていない場合、プロジェクトではエラー イベントを発生し、`Error` タスクの `Text` パラメーターの値をログに記録します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)