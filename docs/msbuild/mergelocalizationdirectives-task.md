---
title: "MergeLocalizationDirectives Task | Microsoft Docs"
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
  - "localizing XAML [WPF MSBuild], moving comments and attributes to a separate file"
  - "MergeLocalizationDirectives task [WPF MSBuild], parameters"
  - "MergeLocalizationDirectives task [WPF MSBuild]"
  - "moving localization comments and attributes to a separate file [WPF MSBuild]"
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MergeLocalizationDirectives Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> タスクは、1 つ以上の [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] バイナリ形式ファイルのローカリゼーション属性とコメントを、アセンブリ全体で単一のファイルにマージします。  
  
## タスク パラメーター  
  
|パラメーター|Description|  
|------------|-----------------|  
|`GeneratedLocalizationFiles`|必須の **ITaskItem\[\]** 型のパラメーター。<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] バイナリ形式の個々のファイルに対するローカリゼーション ディレクティブ ファイルの一覧を指定します。|  
|`OutputFile`|必須の **String** 型の出力パラメーター。<br /><br /> コンパイルされたローカリゼーション ディレクティブ アセンブリの出力パスを指定します。|  
  
## 解説  
 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] のコンテンツには、ローカリゼーション属性とコメントを追加できます。  [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] のローカリゼーション サポートを使用すると、ローカリゼーション属性とコメントを取り出し、生成されるアセンブリとは別の .loc ファイルに格納できます。  これを行うには、**LocalizationPropertyStorage** 属性を使用します。  ローカリゼーション属性とコメント、および **LocalizationPropertyStorage** の詳細については、「[ローカリゼーション属性とコメント](../Topic/Localization%20Attributes%20and%20Comments.md)」を参照してください。  
  
## 使用例  
 いくつかの [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] バイナリ形式ファイルのローカリゼーション コメントを単一の .loc ファイルにマージする方法を次の例に示します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## 参照  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーション \(WPF\) のビルド](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)