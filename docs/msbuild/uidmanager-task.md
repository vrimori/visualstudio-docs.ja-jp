---
title: "UidManager Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
helpviewer_keywords: 
  - "UidManager task [WPF MSBuild]"
  - "UidManager task [WPF MSBuild], parameters"
  - "managing UIDs when localizing XAML elements [WPF MSBuild]"
  - "localizing XAML elements [WPF MSBuild], managing UIDs"
  - "checking UIDs when localizing XAML elements [WPF MSBuild]"
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UidManager Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.UidManager> タスクは、ソース [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルに含まれるすべての [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 要素をローカライズするために、一意識別子 \(UID\) のチェック、更新、または削除を行います。  
  
## タスク パラメーター  
  
|パラメーター|Description|  
|------------|-----------------|  
|`IntermediateDirectory`|省略可能な **String** 型のパラメーター。<br /><br /> **MarkupFiles** パラメーターによって指定されるソース [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルをバックアップするために使用するディレクトリを指定します。|  
|`MarkupFiles`|必須の **ITaskItem\[\]** 型のパラメーター。<br /><br /> UID のチェック、更新、または削除の対象となるソース [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルを指定します。|  
|`Task`|必須の **String** 型のパラメーター。<br /><br /> 実行する UID 管理タスクを指定します。  有効なオプションは、**Check**、**Update**、または **Remove** です。|  
  
## 使用例  
 次の例では、<xref:Microsoft.Build.Tasks.Windows.UidManager> タスクを使用して、指定したソース [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルに適切な UID を持つ [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 要素が含まれることをチェックします。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## 参照  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーション \(WPF\) のビルド](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [方法 : アプリケーションをローカライズする](../Topic/How%20to:%20Localize%20an%20Application.md)