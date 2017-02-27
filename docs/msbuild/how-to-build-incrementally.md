---
title: "方法 : インクリメンタル ビルドを実行する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "インクリメンタル ビルド"
  - "MSBuild, ビルド (インクリメンタルに)"
  - "MSBuild, インクリメンタル ビルド"
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 方法 : インクリメンタル ビルドを実行する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

大規模なプロジェクトをビルドする場合、既にビルドが済んでいて、最新の状態であるコンポーネントが再びビルドされないようにすることが大切です。  毎回すべてのターゲットをビルドすると、そのたびに膨大な時間がかかってしまいます。  インクリメンタル ビルド \(以前ビルドされなかったターゲットまたは古いターゲットだけをビルドすること\) を可能にするため、[!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) には入力ファイルと出力ファイルのタイムスタンプを比較して、ターゲットをスキップするか、ビルドするか、部分的に再ビルドするかを判断する機能があります。  ただし、入力と出力に一対一の対応関係が存在していることが必要です。  この直接的な対応付けをターゲットが識別できるようにするには変換を使用します。  変換の詳細については、「[変換](../msbuild/msbuild-transforms.md)」を参照してください。  
  
## 入力と出力の指定  
 ターゲットのインクリメンタル ビルドは、入力と出力がプロジェクト ファイルに指定されている場合にのみ実行できます。  
  
#### ターゲットの入力と出力を指定するには  
  
-   `Target` 要素の `Inputs` 属性および `Outputs` 属性を使用します。  次に例を示します。  
  
    ```  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は入力ファイルと出力ファイルのタイムスタンプを比較して、ターゲットをスキップするか、ビルドするか、または部分的に再ビルドするかを判断します。  次の例では、`@(CSFile)` 項目のリストに、hello.exe ファイルよりも新しいファイルが存在する場合に、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] によってターゲットが処理されます。それ以外の場合は、ターゲットはスキップされます。  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 入力と出力をターゲットに指定する場合、各出力を単一の入力に対応付けることができる場合と、入力と出力とを直接対応させることができない場合とがあります。  たとえば、前出の [Csc Task](../msbuild/csc-task.md)の場合、出力ファイル hello.exe はすべての入力ファイルに依存しているため、単一の入力ファイルに対応付けることはできません。  
  
> [!NOTE]
>  入力と出力に直接の対応関係が存在しないターゲットは、入力と出力が一対一で対応するターゲットよりも頻繁にビルドされます。これは、一部の入力ファイルに変更があった場合に、どの出力ファイルを再ビルドすればよいかを [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] が判断できないためです。  
  
 インクリメンタル ビルドに最も適したタスクは、[LC Task](../msbuild/lc-task.md)など、明らかに入力と出力に直接の対応関係が存在するタスクです。`Csc` や [Vbc](../msbuild/vbc-task.md) など、複数の入力ファイルから単一の出力アセンブリを生成するタスクはインクリメンタル ビルドには向きません。  
  
## 使用例  
 次の例では、架空のヘルプ システム用のヘルプ ファイルをビルドするプロジェクトを使用します。  プロジェクトは、.txt ソース ファイルを .content 中間ファイルに変換することで機能します。.content 中間ファイルは XML メタデータ ファイルと結合され、ヘルプ システムが使用する最終的な .help ファイルが作成されます。  プロジェクトは次の架空のタスクを使用します。  
  
-   `GenerateContentFiles` : .txt ファイルを .content ファイルに変換します。  
  
-   `BuildHelp`: .content ファイルと XML メタデータ ファイルを結合して、最終的な .help ファイルをビルドします。  
  
 プロジェクトは変換を使用して、`GenerateContentFiles` タスク内の入力と出力の間に一対一のマッピングを作成します。  詳細については、「[変換](../msbuild/msbuild-transforms.md)」を参照してください。  また、`Output` 要素は、`GenerateContentFiles` タスクからの出力を、`BuildHelp` タスクの入力として自動的に使用するように設定されています。  
  
 このプロジェクト ファイルには、`Convert` ターゲットと `Build` ターゲットの両方が含まれています。  `GenerateContentFiles` タスクと `BuildHelp` タスクは、個々のターゲットがインクリメンタル方式でビルドされるように、それぞれ `Convert` ターゲットと `Build` ターゲットに配置されています。  `Output` 要素を使用することにより、`GenerateContentFiles` タスクの出力が `ContentFile` 項目のリストに置かれ、それらが `BuildHelp` タスクの入力として使用されます。  このように `Output` 要素を使用することで、あるタスクからの出力が別のタスクの入力として自動的に渡されます。個々の項目または項目のリストを、タスクごとに手動で列挙する必要はありません。  
  
> [!NOTE]
>  `GenerateContentFiles` ターゲットはインクリメンタル方式でビルドできますが、そのターゲットからの出力はすべて、`BuildHelp` ターゲットの入力として常に必要となります。  `Output` 要素を使用した場合、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は、一方のターゲットからのすべての出力を自動的にもう一方のターゲットの入力として渡します。  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## 参照  
 [ターゲット](../msbuild/msbuild-targets.md)   
 [Target 要素 \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [変換](../msbuild/msbuild-transforms.md)   
 [Csc Task](../msbuild/csc-task.md)   
 [Vbc Task](../msbuild/vbc-task.md)