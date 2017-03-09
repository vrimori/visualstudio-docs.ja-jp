---
title: "Exec Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Exec"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Exec task [MSBuild]"
  - "MSBuild, Exec task"
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Exec Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定された引数を使用して、指定されたプログラムまたはコマンドを実行します。  
  
## パラメーター  
 `Exec` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`Command`|必須の `String` 型のパラメーターです。<br /><br /> 実行するコマンドです。  attrib などのシステム コマンド、または program.exe、runprogram.bat、setup.msi などの実行可能ファイルを指定できます。<br /><br /> このパラメーターには、複数のコマンド行を含めることができます。  または、複数のコマンドをバッチ ファイルに記述し、このパラメーターを使用して実行することもできます。|  
|`CustomErrorRegularExpression`|省略可能な `String` 型のパラメーターです。<br /><br /> ツール出力でエラー行を見つけるために使用される正規表現を指定します。  これは、通常とは異なる形式の出力を生成するツールに対して役立ちます。|  
|`CustomWarningRegularExpression`|省略可能な `String` 型のパラメーターです。<br /><br /> ツール出力で警告行を見つけるために使用される正規表現を指定します。  これは、通常とは異なる形式の出力を生成するツールに対して役立ちます。|  
|`ExitCode`|省略可能な `Int32` 型の読み取り専用出力パラメーターです。<br /><br /> 実行したコマンドの終了コードを示します。|  
|`IgnoreExitCode`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、実行したコマンドの終了コードはタスクで無視されます。  それ以外の場合に、実行したコマンドが 0 以外の終了コードを返すと、タスクは `false` を返します。|  
|`IgnoreStandardErrorWarningFormat`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `false` の場合、出力で標準のエラーおよび警告の形式と一致する行を選択し、それらをエラーおよび警告としてログに記録します。  `true` の場合、この動作が無効になります。|  
|`Outputs`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> タスクの出力アイテムが含まれます。  このパラメーターは、`Exec` タスク自体が設定するわけではありません。  代わりにユーザー側で、タスクで設定されたかのようにこの値を設定でき、プロジェクトの以降の処理で使用できます。|  
|`StdErrEncoding`|省略可能な `String` 型の出力パラメーターです。<br /><br /> タスクの標準エラー ストリームをキャプチャするときのエンコーディングを指定します。  既定値は、現在のコンソール出力のエンコーディングです。|  
|`StdOutEncoding`|省略可能な `String` 型の出力パラメーターです。<br /><br /> タスクの標準出力ストリームをキャプチャするときのエンコーディングを指定します。  既定値は、現在のコンソール出力のエンコーディングです。|  
|`WorkingDirectory`|省略可能な `String` 型のパラメーターです。<br /><br /> コマンドを実行するディレクトリを指定します。|  
  
## 解説  
 このタスクは、実行する必要のあるジョブに対応する固有の [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクが存在しない場合に役立ちます。  ただし、固有のタスクとは異なり、`Exec` タスクでは、実行したツールやコマンドの出力を収集できません。  
  
 `Exec` タスクは、直接プロセスを呼び出す代わりに cmd.exe を呼び出します。  
  
 このドキュメントに記載されているパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.ToolTaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.ToolTask> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)」を参照してください。  
  
## 使用例  
 `Exec` タスクを使用してコマンドを実行する例を次に示します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)