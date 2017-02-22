---
title: "ターゲットのバッチの項目メタデータ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バッチ [MSBuild]"
  - "MSBuild, ターゲットのバッチ"
  - "ターゲットのバッチ [MSBuild]"
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ターゲットのバッチの項目メタデータ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] には、ビルド ターゲットの入力および出力で依存関係の分析を行う機能が用意されています。  ターゲットの入力または出力が最新であると判断された場合、ターゲットはスキップされ、ビルドが続行されます。  `Target` 要素は `Inputs` および `Outputs` 属性を使用して、依存関係の分析中に検査する項目を指定します。  
  
 ターゲットにバッチされた項目を入力または出力として使用するタスクが含まれている場合、ターゲットの `Target` 要素は、その `Inputs` または `Outputs` 属性でバッチを使用して、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] を有効にし、既に最新になっている項目のバッチをスキップする必要があります。  
  
## ターゲットのバッチ  
 次の例には、`Res` という名前の項目のリストが含まれています。これは、`Culture` 項目メタデータに基づいて、2 つのバッチに分割されています。  これらのバッチはそれぞれ、`AL` タスクに渡されます。このタスクは、各バッチの出力アセンブリを作成します。  `Target` 要素の `Outputs` 属性でバッチを使用することにより、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] はターゲットを実行する前に、各バッチが最新かどうかを確認できます。  ターゲットのバッチを使用しないと、項目の両方のバッチは、ターゲットが実行されるたびにタスクによって実行されます。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## 参照  
 [方法 : インクリメンタル ビルドを実行する](../msbuild/how-to-build-incrementally.md)   
 [バッチ](../msbuild/msbuild-batching.md)   
 [Target 要素 \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [タスクのバッチの項目メタデータ](../msbuild/item-metadata-in-task-batching.md)