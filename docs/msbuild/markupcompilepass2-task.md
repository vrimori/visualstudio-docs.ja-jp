---
title: "MarkupCompilePass2 Task | Microsoft Docs"
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
  - "performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task"
  - "MarkupCompilePass2 task [WPF MSBuild]"
  - "MarkupCompilePass2 task [WPF MSBuild], parameters"
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MarkupCompilePass2 Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> タスクは、同じプロジェクト内の型を参照する [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] ファイルに対して、2 番目のマークアップ コンパイル パスを実行します。  
  
## タスク パラメーター  
  
|パラメーター|Description|  
|------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|省略可能な **Boolean** 型のパラメーター。<br /><br /> タスクを別の <xref:System.AppDomain> で実行するかどうかを指定します。  このパラメーターが **false** を返す場合、タスクは [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] と同じ <xref:System.AppDomain> 内で、より高速に実行されます。  このパラメーターが **true** を返す場合、タスクは [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] から分離された 2 番目の <xref:System.AppDomain> 内で実行され、動作はより低速になります。|  
|`AssembliesGeneratedDuringBuild`|省略可能な **String\[\]** 型のパラメーター。<br /><br /> ビルド処理時に変更されるアセンブリへの参照を指定します。  たとえば、[!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] ソリューションには、別のプロジェクトのコンパイル済み出力を参照するプロジェクトが含まれていることがあります。  この場合、別のプロジェクトのコンパイル済み出力を **AssembliesGeneratedDuringBuild** に追加できます。<br /><br /> メモ: **AssembliesGeneratedDuringBuild** は、ビルド ソリューションによって生成されるアセンブリの完全なセットへの参照を含んでいる必要があります。|  
|`AssemblyName`|必須の **String** 型のパラメーター。<br /><br /> プロジェクトのために生成されるアセンブリの短い名前を指定します。  たとえば、プロジェクトが **WinExeAssembly.exe** という名前の [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] 実行可能ファイルを生成する場合、**AssemblyName** パラメーターの値は **WinExeAssembly** になります。|  
|`GeneratedBaml`|省略可能な **ITaskItem\[\]** 型の出力パラメーター。<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] バイナリ形式で生成されたファイルの一覧を含みます。|  
|`KnownReferencePaths`|省略可能な **String\[\]** 型のパラメーター。<br /><br /> ビルド処理時に変更されないアセンブリへの参照を指定します。  [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)]、[!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] インストール ディレクトリなどにあるアセンブリが含まれます。|  
|`Language`|必須の **String** 型のパラメーター。<br /><br /> コンパイラがサポートするマネージ言語を指定します。  有効なオプションは**C\#VBJScript** と **C\+\+** です。|  
|`LocalizationDirectivesToLocFile`|省略可能な **String** 型のパラメーター。<br /><br /> 各ソース [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルのローカリゼーション情報を生成する方法を指定します。  有効なオプションは、**None**、**CommentsOnly**、および **All** です。|  
|`OutputPath`|必須の **String** 型のパラメーター。<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] バイナリ形式ファイルが生成されるディレクトリを指定します。|  
|`OutputType`|必須の **String** 型のパラメーター。<br /><br /> プロジェクトで生成されるアセンブリの型を指定します。  有効なオプションは、**winexe**、**exe**、**library**、および **netmodule** です。|  
|`References`|省略可能な **ITaskItem\[\]** 型のパラメーター。<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイル内で使用される型を含む、ファイルからアセンブリへの参照の一覧を指定します。  そのうちの 1 つは、<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> タスクによって生成されたアセンブリへの参照です。このタスクは、<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> タスクの前に実行しておく必要があります。|  
|`RootNamespace`|省略可能な **String** 型のパラメーター。<br /><br /> プロジェクト内部にあるクラスのルート名前空間を指定します。  **RootNamespace** は、対応する [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルが `x:Class` 属性を含まない場合に、生成されるマネージ コード ファイルの既定の名前空間としても使用されます。|  
|`XAMLDebuggingInformation`|省略可能な **Boolean** 型のパラメーター。<br /><br /> **true** の場合、デバッグを支援するための診断情報が生成され、コンパイルされた [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 内に追加されます。|  
  
## 解説  
 **MarkupCompilePass2** を実行する前に、マークアップ コンパイル パスが延期された [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルによって使用される型を含む、一時アセンブリを生成する必要があります。  一時アセンブリを生成するには、**GenerateTemporaryTargetAssembly** タスクを実行します。  
  
 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> の実行時には、生成された一時アセンブリへの参照を指定します。これにより、最初のマークアップ コンパイル パスでコンパイルが延期された [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルをバイナリ形式にコンパイルできるようになります。  
  
## 使用例  
 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> タスクを使用して 2 番目のコンパイル パスを実行する方法を次の例に示します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
  </Target>  
</Project>  
```  
  
## 参照  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーション \(WPF\) のビルド](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [WPF XAML ブラウザー アプリケーションの概要](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)