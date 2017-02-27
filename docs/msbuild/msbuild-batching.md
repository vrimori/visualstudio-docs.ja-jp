---
title: "MSBuild バッチ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バッチ [MSBuild]"
  - "MSBuild, バッチ処理"
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# MSBuild バッチ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] では、項目メタデータに基づいて項目のリストをさまざまなカテゴリ \(バッチ\) に分割し、バッチごとにターゲットまたはタスクを 1 回実行できます。  
  
## タスクのバッチ  
 タスクのバッチを使用すると、項目のリストをさまざまなバッチに分割して、各バッチを個別にタスクに渡すことによって、プロジェクト ファイルを簡略化できます。  これは、プロジェクト ファイルでタスクとその属性を、複数回実行できるものであっても一度だけ宣言する必要があることを意味します。  
  
 %\(*ItemMetaDataName*\) 表記をいずれかのタスク属性で使用して、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] でタスクのバッチを実行することを指定します。  次の例は、`Color` 項目メタデータ値に基づいて `Example` 項目のリストをバッチに分割し、各バッチを個別に `MyTask` タスクに渡します。  
  
> [!NOTE]
>  タスク属性で項目のリストを参照しない場合や、メタデータ名があいまいな場合は、%\(*ItemCollection.ItemMetaDataName*\) 表記を使用すると、バッチに使用する項目メタデータ値を完全に修飾できます。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 より詳細なバッチの例については、「[タスクのバッチの項目メタデータ](../msbuild/item-metadata-in-task-batching.md)」を参照してください。  
  
## ターゲットのバッチ  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は、ターゲットの入力および出力が最新かどうかを確認してから、ターゲットを実行します。  入力と出力の両方が最新である場合、ターゲットはスキップされます。  ターゲット内のタスクがバッチを使用する場合、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は項目の各バッチの入力および出力が最新かどうかを確認する必要があります。  最新でない場合、ターゲットはヒットするたびに実行されます。  
  
 次の例に %\(*ItemMetaDataName*\) 表記の `Outputs` 属性を含む `Target` 要素を示します。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は、`Color` 項目メタデータに基づいて `Example` 項目のリストをバッチに分割し、各バッチの出力ファイルのタイムスタンプを分析します。  バッチからの出力が最新でない場合は、ターゲットが実行されます。  最新である場合は、ターゲットはスキップされます。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 ターゲットのバッチの別の例については、「[ターゲットのバッチの項目メタデータ](../msbuild/item-metadata-in-target-batching.md)」を参照してください。  
  
## メタデータを使用するプロパティ関数  
 バッチは、メタデータを含むプロパティ関数によって制御できます。  次に例を示します。  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 このコードは、<xref:System.IO.Path.Combine%2A> を使用して、ルート フォルダー パスを Compile の項目パスと結合します。  
  
 プロパティ関数は、メタデータ値の内部には記述できません。  次に例を示します。  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 このようなコードは許可されません。  
  
 プロパティ関数の詳細については、「[プロパティ関数](../msbuild/property-functions.md)」を参照してください。  
  
## 参照  
 [ItemMetadata Element \(MSBuild\)](../msbuild/itemmetadata-element-msbuild.md)   
 [MSBuild の概念](../msbuild/msbuild-concepts.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [詳細な概念](../msbuild/msbuild-advanced-concepts.md)