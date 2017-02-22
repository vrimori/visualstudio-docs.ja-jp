---
title: "MSBuild タスク | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#MSBuild"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild タスク [MSBuild]"
  - "MSBuild、MSBuild タスク"
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild タスク
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

他の [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトから [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトをビルドします。  
  
## パラメーター  
 `MSBuild` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|------------|--------|  
|`BuildInParallel`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、可能な場合、`Projects` パラメーターに指定されたプロジェクトが同時にビルドされます。  既定値は `false` です。|  
|`Projects`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> ビルドするプロジェクト ファイルを指定します。|  
|`Properties`|省略可能な `String` 型のパラメーターです。<br /><br /> 子プロジェクトにグローバル プロパティとして適用するプロパティ名と値のペアを、セミコロン \(;\) で区切って指定します。  このパラメーターを指定することは、[MSBuild.exe](../msbuild/msbuild-command-line-reference.md) でビルドするときに **\/property** スイッチでプロパティを設定することと同じ意味になります。  次に例を示します。<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> `Properties` パラメーター経由でプロジェクトにプロパティを渡すと、プロジェクト ファイルが既に読み込まれている場合でも、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] はプロジェクトの新しいインスタンスを作成します。  プロジェクトの新しいインスタンスが作成されると、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] はそのインスタンスを、異なるグローバル プロパティを持ち、プロジェクトの他のインスタンスと同時にビルド可能な別のプロジェクトとして扱います。  たとえば、リリース構成をデバッグ構成と同時にビルドできます。|  
|`RebaseOutputs`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、ビルドするプロジェクトからのターゲットの出力アイテムの相対パスは、呼び出し元プロジェクトからの相対パスに合わせられます。  既定値は `false` です。|  
|`RemoveProperties`|省略可能な `String` 型のパラメーターです。<br /><br /> 削除するグローバル プロパティのセットを指定します。|  
|`RunEachTargetSeparately`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクでは、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に渡された一覧内のターゲットが \(同時にではなく\) 1 つずつ起動されます。  このパラメーターを `true` に設定すると、前に起動したターゲットが失敗しても、以降のターゲットは起動されることが保証されます。  それ以外の場合は、ビルド エラーが発生すると、以降のターゲットの起動は停止されます。  既定値は `false` です。|  
|`SkipNonexistentProjects`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、ディスク上に存在しないプロジェクト ファイルはスキップされます。  それ以外の場合は、そのようなプロジェクトによりエラーが発生します。|  
|`StopOnFirstFailure`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、プロジェクトの 1 つがビルドに失敗すると、それ以上のプロジェクトはビルドされません。  この機能は現在、平行ビルド \(複数のプロセッサを使用\) の際にはサポートされません。|  
|`TargetAndPropertyListSeparators`|省略可能な `String[]` 型のパラメーターです。<br /><br /> `Project` 項目メタデータとしてターゲットおよびプロパティのリストを指定します。  区切り記号は、処理の前にエスケープ解除されます。  たとえば.. %3B \(エスケープする; " \) は "エスケープすると同じように扱われます; "。|  
|`TargetOutputs`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の読み取り専用出力パラメーターです。<br /><br /> すべてのプロジェクト ファイルからビルドされたターゲットの出力を返します。  指定したターゲットの出力だけが戻ります。指定したターゲットが依存するターゲットが存在しても、それらのターゲットの出力は戻りません。<br /><br /> `TargetOutputs` パラメーターには、次のメタデータも含まれます。<br /><br /> -   `MSBuildSourceProjectFile`: 出力を設定するターゲットを含む [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルです。<br />-   `MSBuildSourceTargetName`: 出力を設定するターゲットです。 **Note:**  各プロジェクト ファイルまたはターゲットの出力を分けるには、プロジェクト ファイルまたはターゲットごとに `MSBuild` タスクを実行します。  `MSBuild` タスクを 1 度だけ実行してすべてのプロジェクト ファイルをビルドすると、すべてのターゲットが 1 つの配列に格納されます。|  
|`Targets`|省略可能な `String` 型のパラメーターです。<br /><br /> ターゲットや、プロジェクト ファイルでビルドするターゲットを指定します。  ターゲット名の一覧を区切るには、セミコロン \(;\) を使用します。  `MSBuild` タスクにターゲットを指定しない場合は、プロジェクト ファイルで指定されている既定のターゲットがビルドされます。 **Note:**  ターゲットは、すべてのプロジェクト ファイルに必要です。  ターゲットが存在しない場合は、ビルド エラーが発生します。|  
|`ToolsVersion`|省略可能な `String` 型のパラメーターです。<br /><br /> このタスクに渡されたプロジェクトのビルド時に使用する `ToolsVersion` を指定します。<br /><br /> プロジェクトで指定されたものとは異なる、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の別のバージョンを対象とするプロジェクトをビルドする [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクを有効にします。  有効な値は `2.0`、`3.0`、および `3.5` です。  既定値は `3.5` です。|  
|`UnloadProjectsOnCompletion`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、操作が完了したらプロジェクトはアンロードされます。|  
|`UseResultsCache`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、キャッシュされた結果が返されます \(ある場合\)。  MSBuild タスクが実行された場合、その結果は、ビルドされた項目のリストとしてスコープ \(\(ProjectFileName, GlobalProperties\)\[TargetNames\]\)<br /><br /> にキャッシュされます。|  
  
## 解説  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
 [Exec Task](../msbuild/exec-task.md)を使用して MSBuild.exe を起動する場合と異なり、このタスクでは、同じ [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロセスで子プロジェクトがビルドされます。  ビルド済みであるためスキップできるターゲットの一覧は、親プロジェクトのビルドと子プロジェクトのビルドの両方で共有されます。  また、新しい [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロセスが作成されないため、このタスクは高速です。  
  
 このタスクでは、プロジェクト ファイルだけでなく、ソリューション ファイルも処理できます。  
  
 プロジェクトを同時にビルドすることを有効にするために [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] によって求められる構成は、構成に \(ポート、プロトコル、タイムアウト、再試行などの\) リモート インフラストラクチャが関連する場合でも、構成ファイルを使用して構成可能にする必要があります。  可能であれば、構成項目を `MSBuild` タスクのタスク パラメーターとして指定できるようにします。  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 以降、ソリューション プロジェクトは、ビルドするすべてのサブプロジェクトから TargetOutputs を出力するようになりました。  
  
## プロジェクトへのプロパティの引き渡し  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 以前のバージョンの [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] では、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 項目に一覧が表示されている別のプロジェクトに対してプロパティの別のセットを渡すことは困難でした。  [MSBuild Task](../msbuild/msbuild-task.md)の Properties 属性を使用すると、[MSBuild Task](../msbuild/msbuild-task.md)をバッチ処理し、項目リスト内の各プロジェクトに対して別のプロパティを条件に応じて用意する場合を除き、その設定はビルド対象のすべてのプロジェクトに適用されました。  
  
 しかし、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 には、新しい予約済みのメタデータ項目が 2 つあります \(Properties および AdditionalProperties\)。これらのメタデータ項目は、[MSBuild Task](../msbuild/msbuild-task.md)を使用してビルドされる別プロジェクトに異なるプロパティを渡すための柔軟な方法を提供します。  
  
> [!NOTE]
>  これらのメタデータ項目は、[MSBuild Task](../msbuild/msbuild-task.md)の Projects 属性に渡される項目に対してのみ適用可能です。  
  
## マルチプロセッサ上でのビルドの利点  
 この新しいメタデータを使用する最大の利点の 1 つは、マルチプロセッサ上でプロジェクトを同時にビルドする場合に見られます。  メタデータを使用することで、すべてのプロジェクトを単一の [MSBuild Task](../msbuild/msbuild-task.md)呼び出しに統合することができます。バッチ処理や条件付き [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] タスクを実行する必要はありません。  単一の [MSBuild Task](../msbuild/msbuild-task.md)だけを呼び出すと、Projects 属性に指定されているすべてのプロジェクトが同時にビルドされます   \(ただし、`BuildInParallel=true` 属性が [MSBuild Task](../msbuild/msbuild-task.md)に指定されている場合に限定されます\)。詳細については、「[複数のプロジェクトの並行ビルド](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)」を参照してください。  
  
## Properties メタデータ  
 一般的なシナリオとして、異なるビルド構成を使用する場合にのみ、[MSBuild Task](../msbuild/msbuild-task.md)を使用して複数のソリューション ファイルをビルドすることが挙げられます。  デバッグ構成を使用してソリューション a1 をビルドし、リリース構成を使用してソリューション a2 をビルドすることができます。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 では、このプロジェクト ファイルは次のようになります。  
  
> [!NOTE]
>  例の中で、"…" はその他のソリューション ファイルを表します。  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 ただし、Properties メタデータを使用すると、次の例に示すように、単一の [MSBuild Task](../msbuild/msbuild-task.md)を使用して簡素化できます。  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 または  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## AdditionalProperties メタデータ  
 [MSBuild Task](../msbuild/msbuild-task.md)を使用して 2 つのソリューション ファイルをビルドするシナリオを考えます。いずれのソリューション ファイルでもリリース構成を使用しますが、一方は x86 アーキテクチャ、もう一方は ia64 アーキテクチャを使用します。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 では、[MSBuild Task](../msbuild/msbuild-task.md)の複数のインスタンスを作成する必要があります。一方は x86 アーキテクチャに基づいたリリース構成を使用してプロジェクトをビルドし、もう一方は ia64 アーキテクチャに基づいたリリース構成を使用してプロジェクトをビルドします。  プロジェクト ファイルは次のようになります。  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 AdditionalProperties メタデータを使用すると、次のコードを使用することによって、単一の [MSBuild Task](../msbuild/msbuild-task.md)を使用して簡素化できます。  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## 使用例  
 次の例では、`MSBuild` タスクを使用して、`ProjectReferences` アイテム コレクションで指定されたプロジェクトをビルドしています。  ターゲットの出力結果は、`AssembliesBuiltByChildProjects` アイテム コレクションに格納されます。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)