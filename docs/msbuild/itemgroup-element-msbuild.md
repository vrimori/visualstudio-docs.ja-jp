---
title: "ItemGroup 要素 (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 38c6099f912424d21df2aeea4cfdd0401ba57465
ms.openlocfilehash: e63c0dd4e201ef83f84f01148aacd4458806103d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/14/2017

---
# ItemGroup 要素 (MSBuild)
<a id="itemgroup-element-msbuild" class="xliff"></a>
ユーザー定義 [Item](../msbuild/item-element-msbuild.md) 要素のセットが含まれます。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトで使用されるすべての項目は、`ItemGroup` 要素の子として指定する必要があります。  
  
 \<Project>  
 \<ItemGroup>  
  
## 構文
<a id="syntax" class="xliff"></a>  
  
```xml  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## 属性および要素
<a id="attributes-and-elements" class="xliff"></a>  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性
<a id="attributes" class="xliff"></a>  
  
|属性|説明|  
|---------------|-----------------|  
|`Condition`|省略可能な属性です。 評価する条件です。 詳細については、「[条件](../msbuild/msbuild-conditions.md)」を参照してください。|  
  
### 子要素
<a id="child-elements" class="xliff"></a>  
  
|要素|説明|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|ビルド プロセスの入力を定義します。 1 つの `ItemGroup` に 0 個以上の `Item` 要素を含めることができます。|  
  
### 親要素
<a id="parent-elements" class="xliff"></a>  
  
|要素|説明|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルの必須のルート要素です。|  
|[Target](../msbuild/target-element-msbuild.md)|.NET Framework 3.5 以降、`Target` 要素の中に `ItemGroup` 要素を使用できるようになりました。 詳細については、[ターゲット](../msbuild/msbuild-targets.md) を参照してください。|  
  
## コメント
<a id="remarks" class="xliff"></a>  
  
## 例
<a id="example" class="xliff"></a>  
 次のコード例は、`ItemGroup` 要素の中で宣言されたユーザー定義の項目コレクション `Res` および `CodeFiles` を示しています。 `Res` 項目コレクション内のそれぞれの項目には、ユーザー定義の子要素 [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) が含まれています。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## 関連項目
<a id="see-also" class="xliff"></a>  
 [プロジェクト ファイル スキーマ リファレンス](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)   
 [MSBuild プロジェクトの共通項目](../msbuild/common-msbuild-project-items.md)
