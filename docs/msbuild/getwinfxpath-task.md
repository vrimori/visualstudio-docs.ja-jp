---
title: "GetWinFXPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "getting the directory of the current .NET Framework runtime [WPF MSBuild]"
  - "GetWinFXPath task [WPF MSBuild], parameters"
  - "GetWinFXPath task [WPF MSBuild]"
  - "obtaining the path to the current .NET Framework runtime [WPF MSBuild]"
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetWinFXPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> タスクは、現在の [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] ランタイムのディレクトリを返します。  
  
## タスク パラメーター  
  
|パラメーター|Description|  
|------------|-----------------|  
|`WinFXPath`|省略可能な **String** 型の出力パラメーター。<br /><br /> [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)] ランタイムへの実際のパスを指定します。|  
|`WinFXNativePath`|必須の **String** 型のパラメーター。<br /><br /> ネイティブ [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] ランタイムへのパスを指定します。|  
|`WinFXWowPath`|必須の **String** 型のパラメーター。<br /><br /> 64 ビット システムの 32 ビット **Windows on Windows** モジュール内の [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] アセンブリへのパスを指定します。|  
  
## 解説  
 <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> タスクが 64 ビット プロセッサで実行されている場合は、**WinFXPath** パラメーターは **WinFXWowPath** パラメーターに保存されているパスに設定されます。その以外の場合は、**WinFXPath** パラメーターは **WinFXNativePath** パラメーターに保存されているパスに設定されます。  
  
## 使用例  
 **GetWinFXPath** タスクを使用して、[!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] ランタイムへのネイティブ パスを検出する例を次に示します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## 参照  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーション \(WPF\) のビルド](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)