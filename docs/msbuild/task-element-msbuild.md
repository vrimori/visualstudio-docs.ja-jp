---
title: "Task Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Task element [MSBuild]"
  - "<Task> element [MSBuild]"
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Task Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクのインスタンスを作成し、実行します。  要素名は、作成しているタスクの名前に従って決定されます。  
  
## 構文  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`Condition`|省略可能な属性です。  評価する条件です。  詳細については、「[Conditions](../msbuild/msbuild-conditions.md)」を参照してください。|  
|`ContinueOnError`|省略可能な属性です。  次の値の1個含めることができます。:<br /><br /> -   **WarnAndContinue** か **true**。  タスクが失敗した場合は、[&#91;ターゲット&#93;](../msbuild/target-element-msbuild.md) の要素とビルドのその後のタスクは実行を継続タスクのすべてのエラーは警告として処理されます。<br />-   **ErrorAndContinue**。  タスクが失敗した場合は、`Target` の要素とビルドのその後のタスクは実行を継続タスクのすべてのエラーはエラーとして扱われます。<br />-   **ErrorAndStop** か **false** \(既定値\)。  タスクが失敗した場合は、`Target` の要素とビルドの残りのタスクは実行されず、`Target` の要素全体とビルドが失敗したと見なされます。<br /><br /> 4.5より前のバージョンの.NET Frameworkは `true` と `false` の値をサポートしていました。<br /><br /> 詳細については、「[方法 : タスクで発生したエラーを無視する](../Topic/How%20to:%20Ignore%20Errors%20in%20Tasks.md)」を参照してください。|  
|`Parameter`|タスク クラスに `[Required]` 属性を持つプロパティが含まれている場合には必ず指定します。<br /><br /> ユーザー定義のタスク パラメーターであり、値としてパラメーター値を持ちます。  `Task` 要素は、パラメーターの各属性がこのタスク クラスの .NET プロパティに対応付けられた、任意の数のパラメーターを持つことができます。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[出力](../msbuild/output-element-msbuild.md)|プロジェクト ファイル内のタスクの出力を格納します。  タスクには 0 個以上の `Output` 要素を設定できます。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[Target](../msbuild/target-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクのコンテナー要素です。|  
  
## 解説  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルの `Task` 要素では、タスクのインスタンスを作成し、このインスタンスにプロパティを設定し、これを実行します。  `Output` 要素では、プロジェクト ファイルの他の場所で使用するために、プロパティやアイテムに出力パラメーターを格納します。  
  
 タスクの親 `Target` 要素に [OnError](../msbuild/onerror-element-msbuild.md) 要素がある場合、このタスクが失敗し、`ContinueOnError` が `false` に設定してあるときには、これらの要素も評価されます。  タスクの詳細については、「[タスク](../msbuild/msbuild-tasks.md)」を参照してください。  
  
## 使用例  
 [Csc タスク](../msbuild/csc-task.md) クラスのインスタンスを作成し、プロパティを 6 個設定し、タスクを実行するコード例を次に示します。  実行が終了すると、オブジェクトの `OutputAssembly` プロパティの値が、`FinalAssemblyName` という名前のアイテム リストに格納されます。  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)