---
title: '&lt;RelatedProducts&gt;要素 (ブートス トラップ) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5701b88f3942301c8fdb6d674fc323e62a93589b
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815458"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt;要素 (ブートス トラップ)
`RelatedProducts`要素は、現在の製品に含まれるかに依存する他の製品を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
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
 `RelatedProducts`要素の子では、`Product`要素。 属性ではありません。  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct`要素は、名前付きの製品では、現在の製品が依存することと、現在の 1 つ前に、指定された製品をインストールすることを示します。 子である、`RelatedProducts`要素。 A`RelatedProducts`要素が 1 つまたは複数あります`DependsOnProduct`要素。  
  
 `DependsOnProduct` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Code`|指定したとおり、含まれる製品のコードの名前、`ProductCode`の属性、`Product`要素。 詳細については、次を参照してください。 [ \<Product > 要素](../deployment/product-element-bootstrapper.md)です。|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts`要素は、0 個以上を定義します。`DependsOnProduct`要素、属性を持っていないとします。 少なくとも 1 つ`DependsOnProduct`このセットには、現在の製品する前にインストールする必要があります。 A`RelatedProducts`要素が 0 以上を持つ`EitherProducts`要素。  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct`要素場合、その製品は現在のインストールに付属の独立したインストールは不要です。 子である、`RelatedProducts`要素。 A`RelatedProducts`要素が 1 つまたは複数あります`IncludesProduct`要素。  
  
 `IncludesProduct` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Code`|指定したとおり、含まれる製品のコードの名前、`ProductCode`の属性、`Product`要素。 詳細については、次を参照してください。 [ \<Product > 要素](../deployment/product-element-bootstrapper.md)です。|  
  
## <a name="example"></a>例  
 次のコード例と Microsoft インストーラーがインストールされていることを指定します、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]、ため、個別のインストールは必要ありません。  
  
```xml  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>関連項目  
 [\<Product > 要素](../deployment/product-element-bootstrapper.md)