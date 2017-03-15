---
title: "方法: ターゲットとタスクを構成する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: ac979e7287046164db37848778f648656f7230a6
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-configure-targets-and-tasks"></a>方法 : ターゲットとタスクを構成する
一部の MSBuild タスクは、開発コンピューターの環境に関係なく、それがターゲットとする環境で実行されるように設定できます。 たとえば、64 ビット コンピューターを使用し、32 ビット アーキテクチャをターゲットとするアプリケーションを構築するとき、一部のタスクが 32 ビット プロセスで実行されます。  
  
> [!NOTE]
>  ビルド タスクが Visual C# や Visual Basic のような .NET 言語で記述されており、ネイティブのリソースまたはツールを使用しない場合、調整なしで、あらゆるターゲット コンテンツで実行されます。  
  
## <a name="usingtask-attributes-and-task-parameters"></a>UsingTask 属性とタスク パラメーター  
 次の `UsingTask` 属性は、特定のビルド プロセスで、あるタスクのすべての操作に影響を与えます。  
  
-   `Runtime` 属性は、それが存在する場合、共通言語ランタイム (CLR) バージョンを設定し、値として `CLR2`、`CLR4`、`CurrentRuntime`、`*` (任意のランタイム) のいずれかを取得します。  
  
-   `Architecture` 属性は、それが存在する場合、プラットフォームとビット数を設定し、値として `x86`、`x64`、`CurrentArchitecture`、`*` (任意のアーキテクチャ) のいずれかを取得します。  
  
-   `TaskFactory` 属性は、それが存在する場合、タスク インスタンスを作成して実行するタスク ファクトリを設定し、値として `TaskHostFactory` のみを取得します。 詳細については、このドキュメントで後述する「タスク ファクトリ」を参照してください。  
  
```xml  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 `MSBuildRuntime` パラメーターと `MSBuildArchitecture` パラメーターを利用し、個々のタスクのターゲット コンテキストを設定することもできます。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 MSBuild はタスクを実行する前に、一致する (ターゲット コンテキストが同じ) `UsingTask` を探します。  `UsingTask` で指定されているが、該当するタスクにないパラメーターは一致すると見なされます。  タスクで指定されているが、該当する `UsingTask` にないパラメーターも一致すると見なされます。 パラメーター値が `UsingTask` にもタスクにも指定されていない場合、値は既定として `*` (任意のパラメーター) になります。  
  
> [!WARNING]
>  複数の `UsingTask` が存在し、すべてに一致する `TaskName`、`Runtime`、`Architecture` 属性がある場合、最後に評価されたものが他に取って代わります。  
  
 パラメーターがタスクに設定されていると、MSBuild は、それらのパラメーターに一致するか、少なくともそれらと競合しない `UsingTask` を探します。  複数の `UsingTask` が同じタスクのターゲット コンテキストを指定できます。  たとえば、異なるターゲット環境のために異なる実行可能ファイルが与えられているタスクは次のようになります。  
  
```xml  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## <a name="task-factories"></a>タスク ファクトリ  
 MSBuild はタスクを実行する前に、現在のソフトウェア コンテキストで実行するように指定されているかどうかを確認します。  タスクがそのように指定されている場合、MSBuild は AssemblyTaskFactory にタスクを渡します。AssemblyTaskFactory はタスクを現在のプロセスで実行します。現在のプロセスで実行するように指定されていない場合、MSBuild は TaskHostFactory にタスクを渡します。TaskHostFactory は、ターゲット コンテキストに一致するプロセスでタスクを実行します。 現在のコンテキストとターゲット コンテキストが一致する場合でも、`TaskFactory` を `TaskHostFactory` に設定することで、プロセスの外でタスクを実行するように強制できます (隔離、セキュリティ、またはその他の理由から)。  
  
```xml  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>ファントム タスク パラメーター  
 他のタスク パラメーターと同様に、`MSBuildRuntime` と `MSBuildArchitecture` はビルド プロパティから設定できます。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```xml  
  
 Unlike other task parameters, `MSBuildRuntime` and `MSBuildArchitecture` are not apparent to the task itself.  To write a task that is aware of the context in which it runs, you must either test the context by calling the .NET Framework, or use build properties to pass the context information through other task parameters.  
  
> [!NOTE]
>  `UsingTask` attributes can be set from toolset and environment properties.  
  
 The `MSBuildRuntime` and `MSBuildArchitecture` parameters provide the most flexible way to set the target context, but also the most limited in scope.  On the one hand, because they are set on the task instance itself and are not evaluated until the task is about to run, they can derive their value from the full scope of properties available at both evaluation-time and build-time.  On the other hand, these parameters only apply to a particular instance of a task in a particular target.  
  
> [!NOTE]
>  Task parameters are evaluated in the context of the parent node, not in the context of the task host.Environment variables that are runtime- or architecture- dependent (such as the Program files location) will evaluate to the value that matches the parent node.  However, if the same environment variable is read directly by the task, it will correctly be evaluated in the context of the task host.  
  
## See Also  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)
