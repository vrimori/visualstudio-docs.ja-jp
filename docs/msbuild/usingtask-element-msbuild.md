---
title: "UsingTask Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#UsingTask"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "UsingTask element [MSBuild]"
  - "<UsingTask> element [MSBuild]"
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# UsingTask Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[Task](../msbuild/task-element-msbuild.md) 要素で参照されているタスクを、タスクの実装が含まれているアセンブリにマップします。  
  
## 構文  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`AssemblyName`|`AssemblyName` 属性と `AssemblyFile` 属性のどちらかが必要です。<br /><br /> 読み込むアセンブリの名前。  `AssemblyName` 属性は厳密な名前付きのアセンブリを受け取りますが、厳密な名前は必須ではありません。  この属性を使用すると、.NET の <xref:System.Reflection.Assembly.Load%2A> メソッドを使用してアセンブリを読み込む場合と同じ結果が得られます。<br /><br /> `AssemblyFile` 属性が使用されている場合、この属性は使用できません。|  
|`AssemblyFile`|`AssemblyName` と `AssemblyFile` 属性のどちらかが必要です。<br /><br /> アセンブリのファイル パス。  この属性は、完全パスまたは相対パスを受け取ります。  相対パスは、`UsingTask` 要素が宣言されているプロジェクト ファイルまたはターゲット ファイルのディレクトリに対して相対的なパスです。  この属性を使用すると、.NET の <xref:System.Reflection.Assembly.LoadFrom%2A> メソッドを使用してアセンブリを読み込む場合と同じ結果が得られます。<br /><br /> `AssemblyName` 属性が使用されている場合、この属性は使用できません。|  
|`TaskFactory`|省略可能な属性です。<br /><br /> 指定された `Task` 名のインスタンスの生成を担うアセンブリ内のクラスを指定します。  ユーザーは、タスク ファクトリが受信してタスクの生成に使用する子要素として、`TaskBody` を指定することもできます。  `TaskBody` の内容は、タスク ファクトリに固有のものです。|  
|`TaskName`|必須の属性です。<br /><br /> アセンブリから参照するタスクの名前。  あいまいになる可能性がある場合、この属性は常に完全な名前空間を指定する必要があります。  あいまいさが存在する場合、MSBuild によって任意の一致が選択され、予期しない結果につながる可能性があります。|  
|`Condition`|省略可能な属性です。<br /><br /> 評価する条件です。  詳細については、「[Conditions](../msbuild/msbuild-conditions.md)」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|指定された `TaskFactory` によって生成されるタスクに表示されるパラメーターのセットです。|  
|[タスク](../msbuild/task-element-msbuild.md)|タスクのインスタンスを生成するために `TaskFactory` に渡されるデータです。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[プロジェクト](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルの必須のルート要素です。|  
  
## 解説  
 環境変数、コマンド ライン プロパティ、およびプロジェクト レベル プロパティは、明示的に、またはインポートされたプロジェクト ファイルを通じてプロジェクト ファイル内に表示されている限り、`UsingTask` 要素内の任意の場所から参照できます。  詳細については、「[タスク](../msbuild/msbuild-tasks.md)」を参照してください。  
  
> [!NOTE]
>  MSBuild エンジンを使用してグローバルに登録された .tasks ファイルの 1 つから `UsingTask` 要素が使用されている場合、プロジェクトレベル プロパティは意味を持ちません。  プロジェクト レベル プロパティは、MSBuild に対してグローバルなプロパティではありません。  
  
 MSBuild 4.0 では、UsingTask を .overridetask ファイルから読み込むことができます。  
  
## 使用例  
 次の例では、`AssemblyName` 属性で `UsingTask` 要素を使用する方法を示します。  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## 使用例  
 次の例では、`AssemblyFile` 属性で `UsingTask` 要素を使用する方法を示します。  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)