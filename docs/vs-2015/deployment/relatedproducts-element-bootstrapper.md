---
title: '&lt;RelatedProducts&gt;要素 (ブートス トラップ) |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ee65c4e4cacd4680256e34583559d74935a89e3b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534750"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt;要素 (ブートス トラップ)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ &lt;RelatedProducts&gt;要素 (ブートス トラップ)](https://docs.microsoft.com/visualstudio/deployment/relatedproducts-element-bootstrapper)します。  
  
`RelatedProducts`要素は、現在の製品に含まれるかに依存する他の製品を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `RelatedProducts`要素の子である、`Product`要素。 属性ではありません。  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct`要素は、現在の製品は、名前付きの製品によって異なり、現在の前に、名前付きの製品をインストールすることを示します。 子である、`RelatedProducts`要素。 A`RelatedProducts`要素が 1 つまたは複数あります`DependsOnProduct`要素。  
  
 `DependsOnProduct` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Code`|指定したとおり、含まれる製品のコードの名前、`ProductCode`の属性、`Product`要素。 詳細については、次を参照してください。 [\<製品 > 要素](../deployment/product-element-bootstrapper.md)します。|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts`要素は、0 個以上を定義します。`DependsOnProduct`要素、属性を持っていません。 少なくとも 1 つ`DependsOnProduct`このセットでは、現在の製品する前にインストールする必要があります。 A `RelatedProducts` 0 個以上の要素を持つことができます`EitherProducts`要素。  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct`要素は、製品は現在のインストールに含まれているし、個別のインストールが必要としないことを示します。 子である、`RelatedProducts`要素。 A`RelatedProducts`要素が 1 つまたは複数あります`IncludesProduct`要素。  
  
 `IncludesProduct` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Code`|指定したとおり、含まれる製品のコードの名前、`ProductCode`の属性、`Product`要素。 詳細については、次を参照してください。 [\<製品 > 要素](../deployment/product-element-bootstrapper.md)します。|  
  
## <a name="example"></a>例  
 次のコード例で、Microsoft インストーラーがインストールされていることを指定します、 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]、ため、個別のインストールは必要ありません。  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>関連項目  
 [\<製品 > 要素](../deployment/product-element-bootstrapper.md)



