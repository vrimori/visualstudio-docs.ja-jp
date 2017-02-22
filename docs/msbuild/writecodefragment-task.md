---
title: "WriteCodeFragment Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "MSBuild, WriteCodeFragment task"
  - "WriteCodeFragment task [MSBuild]"
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteCodeFragment Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定した生成されたコードのフラグメントの一時コード ファイルを生成します。  ファイルは削除されません。  
  
## パラメーター  
 `WriteCodeFragment` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`AssemblyAttributes`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 記述する属性の説明。  項目 `Include` の値は、属性の完全な型名 \("System.AssemblyVersionAttribute" など\) です。<br /><br /> 各メタデータはパラメーターの名前と値のペアであり、これは `String` 型である必要があります。  一部の属性では、位置指定コンストラクター引数のみが許可されます。  ただし、これらの引数はいずれの属性でも使用できます。  位置指定コンストラクター属性を設定するには、"\_Parameter1"、"\_Parameter2" のようなメタデータ名を使用します。<br /><br /> パラメーター インデックスは省略できません。|  
|`Language`|必須の `String` 型のパラメーターです。<br /><br /> 生成するコードの言語を指定します。<br /><br /> `Language` では、"C\#"、"VisualBasic" など、CodeDom プロバイダーが使用可能な任意の言語を指定できます。  生成されるファイルは、該当する言語の既定のファイル名拡張子を持ちます。|  
|`OutputDirectory`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> 生成されたコードの出力先フォルダーを指定します。通常は中間フォルダーです。|  
|`OutputFile`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型の出力パラメーターです。<br /><br /> 生成されたファイルのパスを指定します。  ファイル名を使用してこのパラメーターを設定する場合は、出力先のフォルダーがファイル名の先頭に付加されます。  ルートを使用して設定する場合は、出力先のフォルダーは無視されます。<br /><br /> このパラメーターを設定しない場合、出力ファイル名は、出力先フォルダー、任意のファイル名、および指定した言語の既定のファイル名拡張子となります。|  
  
## 解説  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)