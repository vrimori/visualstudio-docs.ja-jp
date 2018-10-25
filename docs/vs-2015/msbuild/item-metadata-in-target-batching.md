---
title: ターゲットのバッチの項目メタデータ | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 011bb9b738aa135fd14c4dbddfb26f9cea2f7bd1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232689"
---
# <a name="item-metadata-in-target-batching"></a>ターゲットのバッチの項目メタデータ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] では、ビルド ターゲットの入力と出力の依存関係分析を分析できます。 ターゲットの入力または出力が最新の状態であると判断された場合、ターゲットはスキップされ、ビルドが進行します。 `Target` 要素は `Inputs` 属性と `Outputs` 属性を利用し、依存関係分析中に検査する項目を指定します。  
  
 入力または出力としてバッチの項目を利用するタスクがターゲットに含まれる場合、ターゲットの `Target` 要素では、既に最新の状態になっている項目のバッチを [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] でスキップするために、その `Inputs` または `Outputs` 属性でバッチ処理を利用する必要があります。  
  
## <a name="batching-targets"></a>ターゲットのバッチ処理  
 次の例には、`Culture` 項目メタデータに基づいて 2 つのバッチに分割されている `Res` という名前の項目一覧が含まれています。 これらのバッチのいずれも `AL` タスクに渡されます。このタスクで、バッチごとに出力アセンブリが作成されます。 `Target` 要素の `Outputs` 属性でバッチ処理を利用することで、[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] では、ターゲットを実行する前に、個々のバッチが最新の状態になっているか判断できます。 ターゲットのバッチ処理を利用しないと、ターゲットが実行されるたびに項目の両方のバッチが実行されます。  
  
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
  
## <a name="see-also"></a>関連項目  
 [方法 : インクリメンタル ビルドを実行する](../msbuild/how-to-build-incrementally.md)   
 [バッチ](../msbuild/msbuild-batching.md)   
 [Target 要素 (MSBuild)](../msbuild/target-element-msbuild.md)   
 [タスクのバッチの項目メタデータ](../msbuild/item-metadata-in-task-batching.md)



