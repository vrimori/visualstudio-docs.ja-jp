---
title: "LC Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#LC"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, LC task"
  - "LC task [MSBuild]"
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LC Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このタスクは LC.exe をラップします。LC.exe は、.licx ファイルから .license ファイルを生成します。  LC.exe の詳細については、「[Lc.exe \(ライセンス コンパイラ\)](../Topic/Lc.exe%20\(License%20Compiler\).md)」を参照してください。  
  
## パラメーター  
 `LC` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`LicenseTarget`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> .licenses ファイルを生成する実行可能ファイルを指定します。|  
|`NoLogo`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> Microsoft 著作権情報を表示しません。|  
|`OutputDirectory`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力 .licenses ファイルを格納するディレクトリを指定します。|  
|`OutputLicense`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型の出力パラメーターです。<br /><br /> .licenses ファイルの名前を指定します。  名前を指定しなかった場合には、.licx ファイルの名前が使用され、.licenses ファイルは、.licx ファイルが格納されているディレクトリに作成されます。|  
|`ReferencedAssemblies`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> .license ファイルを生成するときに読み込む、参照先のコンポーネントを指定します。|  
|`SdkToolsPath`|省略可能な `String` 型のパラメーターです。<br /><br /> resgen.exe などの SDK ツールのパスを指定します。|  
|`Sources`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> .licenses ファイルに格納するライセンス済みのコンポーネントが格納してあるアイテムを指定します。  詳細については、「[Lc.exe \(ライセンス コンパイラ\)](../Topic/Lc.exe%20\(License%20Compiler\).md)」にある `/complist` スイッチの説明を参照してください。|  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.ToolTaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.ToolTask> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)」を参照してください。  
  
## 使用例  
 `LC` タスクを使用してライセンスをコンパイルする例を次に示します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)