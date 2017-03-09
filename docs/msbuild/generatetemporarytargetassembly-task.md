---
title: "GenerateTemporaryTargetAssembly Task | Microsoft Docs"
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
  - "build process [WPF MSBuild], XAML page refers to a locally declared type"
  - "GenerateTemporaryTargetAssembly task [WPF MSBuild]"
  - "GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters"
  - "creating an assembly [WPF MSBuild], XAML page refers to a locally declared type"
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateTemporaryTargetAssembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> タスクは、プロジェクト内の少なくとも 1 つの [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] ページが、そのプロジェクトでローカルに宣言されている型を参照している場合に、アセンブリを生成します。  生成されるアセンブリは、ビルド処理が完了するか、またはビルド処理が失敗すると削除されます。  
  
## タスク パラメーター  
  
|パラメーター|Description|  
|------------|-----------------|  
|`AssemblyName`|必須の **String** 型のパラメーター。<br /><br /> プロジェクトのために生成されるアセンブリの短い名前を指定します。この名前は、一時的に生成されるターゲット アセンブリの名前にもなります。  たとえば、プロジェクトが **WinExeAssembly.exe** という名前の [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 実行可能ファイルを生成する場合、**AssemblyName** パラメーターの値は **WinExeAssembly** になります。|  
|`CompileTargetName`|必須の **String** 型のパラメーター。<br /><br /> ソース コード ファイルからアセンブリを生成するために使用される [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] ターゲットの名前を指定します。  **CompileTargetName** の一般的な値は、**CoreCompile** です。|  
|`CompileTypeName`|必須の **String** 型のパラメーター。<br /><br /> **CompileTargetName** パラメーターで指定したターゲットによって実行されるコンパイルの種類を指定します。  **CoreCompile** ターゲットでは、この値は **Compile** です。|  
|`CurrentProject`|必須の **String** 型のパラメーター。<br /><br /> 一時ターゲット アセンブリを必要とするプロジェクトの、[!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] プロジェクト ファイルの完全なパスを指定します。|  
|`GeneratedCodeFiles`|省略可能な **ITaskItem\[\]** 型のパラメーター。<br /><br /> [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) によって生成される言語固有のマネージ コード ファイルの一覧を指定します。|  
|`IntermediateOutputPath`|必須の **String** 型のパラメーター。<br /><br /> 生成される一時ターゲット アセンブリが格納されるディレクトリを指定します。|  
|`MSBuildBinPath`|必須の **String** 型のパラメーター。<br /><br /> 一時ターゲット アセンブリをコンパイルするために必要な **MSBuild.exe** の場所を指定します。|  
|`ReferencePath`|省略可能な **ITaskItem\[\]** 型のパラメーター。<br /><br /> 一時ターゲット アセンブリにコンパイルされる型によって参照されるアセンブリの一覧を、パスおよびファイル名を使用して指定します。|  
|`ReferencePathTypeName`|必須の **String** 型のパラメーター。<br /><br /> コンパイル ターゲット \(**CompileTargetName**\) パラメーターによって使用される、アセンブリ参照の一覧 \(**ReferencePath**\) を指定するパラメーターを指定します。  適切な値は、**ReferencePath** です。|  
  
## 解説  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) によって実行される最初のマークアップ コンパイル パスでは、[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルがバイナリ形式にコンパイルされます。  したがって、コンパイラでは、[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルで使用される型を含んでいる参照アセンブリの一覧が必要になります。  ただし、同じプロジェクト内で定義されている型が [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルで使用されていると、そのプロジェクトの対応するアセンブリは、プロジェクトがビルドされるまで作成されません。  このため、最初のマークアップ コンパイル パスの間にアセンブリ参照を用意することができません。  
  
 代わりに、**MarkupCompilePass1** は、同じプロジェクト内の型への参照を含む [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルの変換を、[MarkupCompilePass2](../msbuild/markupcompilepass2-task.md) によって実行される 2 番目のマークアップ コンパイル パスまで延期します。  **MarkupCompilePass2** が実行される前に、一時アセンブリが生成されます。  このアセンブリには、マークアップ コンパイル パスが延期された [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルによって使用される型が含まれます。  **MarkupCompilePass2** の実行時には、生成された一時アセンブリへの参照を指定します。これにより、コンパイルが延期された [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルをバイナリ形式にコンパイルできるようになります。  
  
## 使用例  
 次の例では、`Page1.xaml` が同じプロジェクト内の型への参照を含んでいるため、一時アセンブリが作成されます。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GenerateTemporaryTargetAssemblyTask">  
    <GenerateTemporaryTargetAssembly  
      AssemblyName="WPFMSBuildSample"  
      CompileTargetName="CoreCompile"  
      CompileTypeName="Compile"  
      CurrentProject="FullBuild.proj"  
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"  
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"  
      IntermediateOutputPath=".\obj\debug\"  
      MSBuildBinPath="$(MSBuildBinPath)"  
      ReferencePathTypeName="ReferencePath"/>  
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