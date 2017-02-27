---
title: "&lt;RelatedProducts&gt; 要素 (ブートストラップ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
  - "MSBuild.GenerateBootstrapper.DuplicateItems"
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
  - "MSBuild.GenerateBootstrapper.DependencyNotFound"
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<RelatedProducts> 要素 [ブートストラップ]"
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# &lt;RelatedProducts&gt; 要素 (ブートストラップ)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`RelatedProducts` 要素では、現在の製品が依存する他の製品、または現在の製品に含まれる他の製品を定義します。  
  
## 構文  
  
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
  
## 要素と属性  
 `RelatedProducts` 要素は、`Product` 要素に必須の子です。  属性はありません。  
  
## DependsOnProduct  
 `DependsOnProduct` 要素では、現在の製品が指定した製品に依存していること、指定した製品を現在の製品より前にインストールする必要があることを示します。  これは `RelatedProducts` 要素の子になります。  `RelatedProducts` 要素は `DependsOnProduct` 要素を 1 つ以上持つことができます。  
  
 `DependsOnProduct` には、以下の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`Code`|含まれている製品のコード名です。`Product` 要素の `ProductCode` 属性で指定されるものです。  詳細については、「[\<Product\> 要素](../deployment/product-element-bootstrapper.md)」を参照してください。|  
  
## EitherProducts  
 `EitherProducts` 要素は、0 個以上の `DependsOnProduct` 要素を定義します。属性はありません。  このセットのうち少なくとも 1 つの `DependsOnProduct` を、現在の製品より前にインストールする必要があります。  `RelatedProducts` 要素は、`EitherProducts` 要素を 0 個以上持つことができます。  
  
## IncludesProduct  
 `IncludesProduct` 要素では、製品は現在のインストールに含まれているため、別途インストールする必要がないことを示します。  これは `RelatedProducts` 要素の子になります。  `RelatedProducts` 要素は `IncludesProduct` 要素を 1 つ以上持つことができます。  
  
 `IncludesProduct` には、以下の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`Code`|含まれている製品のコード名です。`Product` 要素の `ProductCode` 属性で指定されるものです。  詳細については、「[\<Product\> 要素](../deployment/product-element-bootstrapper.md)」を参照してください。|  
  
## 使用例  
 Microsoft インストーラーは [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] と共にインストールされるため、個別にインストールする必要がないことを指定するコード例を次に示します。  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## 参照  
 [\<Product\> 要素](../deployment/product-element-bootstrapper.md)