---
title: "方法 : ターゲットとタスクを構成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : ターゲットとタスクを構成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild 選択したタスクを対象とする環境の実行に開発用コンピューターの環境に関係なく設定できます。  たとえば、 32 ビット アーキテクチャを対象とするアプリケーションをビルドするには、 64 ビット コンピューターを使用すると、選択したタスクは 32 ビット プロセスで動作します。  
  
> [!NOTE]
>  ビルド タスクが Visual C\# などの .NET 言語では、 Visual Basic、および使用するネイティブ リソースまたはツールを記述したら、適合せずに、対象のコンテキストで実行されます。  
  
## UsingTask の属性、タスク パラメーター  
 `UsingTask` の次の属性は、特定のビルド処理のタスクのすべての操作に影響します:  
  
-   `Runtime` の属性が存在する場合、共通言語ランタイムのバージョンを設定 \(CLR\)し、これらの値のいずれかを実行できます: `CLR2`、 `CLR4`、 `CurrentRuntime`、または `*` （すべてのランタイム （CLR）。  
  
-   `Architecture` の属性が存在する場合、プラットフォームとビットを設定し、これらの値のいずれかを実行できます: `x86`、 `x64`、 `CurrentArchitecture`、または `*` （すべてのアーキテクチャ）。  
  
-   `TaskFactory` の属性が存在する場合、タスク インスタンスを設定し、値のみ `TaskHostFactory`作成し、実行するタスク ファクトリを受け取ります。  詳細については、タスク ファクトリが、このドキュメントの後半のセクションを参照してください。  
  
```  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 個々のタスクのターゲットのコンテキストを設定するには `MSBuildRuntime` と `MSBuildArchitecture` パラメーターを使用できます。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 MSBuild は、タスクを実行する前に、同じターゲットのコンテキストがある一致の `UsingTask` を検索します。  `UsingTask` でない対応するタスクで指定されているが、パラメーターが一致すると見なされます。  タスクでない対応する `UsingTask` で指定したが、パラメーターは、一致すると見なされます。  パラメーター値が `UsingTask` またはタスクで指定されていない場合、値は `*` （パラメーター）に設定されます。  
  
> [!WARNING]
>  複数の `UsingTask` があり、すべてとの `TaskName`、 `Runtime`と `Architecture` の属性がの場合、は評価される最後の 1 つが他を置き換えます。  
  
 パラメーターはタスクで設定されている場合、これらのパラメーターに一致する試みますまたは、少なくとも検索ように、これらの競合ではありません。 MSBuild はを `UsingTask` 。  複数の `UsingTask` は、同じタスクの対象のコンテキストを指定できます。  たとえば、異なるターゲット環境ごとに異なる実装があるタスクは、この 1 に類似する可能性があります:  
  
```  
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
  
## タスク ファクトリ  
 これがタスクを実行する前に、現在のソフトウェアのコンテキストで実行するように指定するかどうかを、チェックします。  タスクによって指定されている場合、現在のプロセスで実行する AssemblyTaskFactory に渡し、; それ以外の場合、 MSBuild はターゲットのコンテキストに一致するプロセスのタスクを実行する TaskHostFactory にタスクを渡します。  現在のコンテキストおよび対象のコンテキストが一致した場合でも、 `TaskHostFactory`へ `TaskFactory` を設定することによってプロセス （分離、セキュリティ、またはそのほかの原因の場合）実行するタスクを強制できます。  
  
```  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## 幻影のタスク パラメーター  
 他のタスク パラメーターと同様に、 `MSBuildRuntime` と `MSBuildArchitecture` 、ビルド プロパティで設定できます。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 他のタスク パラメーターとは異なり、 `MSBuildRuntime` と `MSBuildArchitecture` は、タスク自体に明確ではありません。  これが実行されるコンテキストを認識するタスクを作成するには、 .NET Framework を呼び出すことによってコンテキストをテストしたり、他のタスク パラメーターでコンテキスト情報を渡すためにビルド プロパティを使用します。  
  
> [!NOTE]
>  `UsingTask` の 属性は、ツール セットと環境のプロパティから設定できます。  
  
 `MSBuildRuntime` と `MSBuildArchitecture` パラメーターは、ターゲット コンテキストを設定するほとんどのスコープの制限も柔軟に示します。  タスクが実行を開始するまで一方、タスク インスタンス自体で設定され、評価されないので評価時、およびビルド時の両方に使用できるプロパティの完全なスコープから値を取得できます。  一方、これらのパラメーターは、特定のターゲット タスクの特定のインスタンスにのみ適用されます。  
  
> [!NOTE]
>  タスク パラメーターは親ノードのコンテキストではないタスク ホストのコンテキスト内で評価されます。ランタイムであるまたはアーキテクチャ依存は親ノードに一致する値 （プログラム ファイルの場所など）を評価する環境変数。  ただし、同じ環境変数がタスクによって直接読み取られた時点で解放、タスク ホストのコンテキスト内で正しく評価されます。  
  
## 参照  
 [ターゲットとタスクの構成](../msbuild/configuring-targets-and-tasks.md)