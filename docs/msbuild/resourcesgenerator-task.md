---
title: "ResourcesGenerator Task | Microsoft Docs"
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
  - "embedding resources into a .resources file [WPF MSBuild]"
  - "ResourcesGenerator task [WPF MSBuild]"
  - "ResourcesGenerator task [WPF MSBuild], parameters"
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResourcesGenerator Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> タスクは、1 つ以上のリソース \(.jpg、.ico、.bmp、バイナリ形式の [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]、その他の種類の拡張子\) を .resources ファイルに埋め込みます。  
  
## タスク パラメーター  
  
|パラメーター|Description|  
|------------|-----------------|  
|`OutputPath`|必須の **String** 型のパラメーター。<br /><br /> 出力ディレクトリのパスを指定します。  パスが絶対パスではない場合は、プロジェクトのルート ディレクトリに対する相対パスとして扱われます。|  
|`OutputResourcesFile`|必須の **ITaskItem\[\]** 型の出力パラメーター。<br /><br /> 生成される .resources ファイルのパスと名前を指定します。  パスが絶対パスではない場合、.resources ファイルはプロジェクトのルート ディレクトリに対する相対パスに作成されます。|  
|`ResourcesFiles`|必須の **ITaskItem\[\]** 型のパラメーター。<br /><br /> 生成される .resources ファイルに埋め込まれる 1 つ以上のリソースを指定します。|  
  
## 使用例  
 1 つの .bmp リソースを持つ .resources ファイルを作成する例を次に示します。  .bmp リソースは、プロジェクトのルート ディレクトリを基準にした相対ディレクトリに生成されます。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## 参照  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーション \(WPF\) のビルド](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)