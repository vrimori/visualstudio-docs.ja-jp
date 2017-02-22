---
title: "ItemGroup 要素 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemGroup 要素 [MSBuild]"
  - "<ItemGroup> 要素 [MSBuild]"
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ItemGroup 要素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ユーザーが定義する、一連の [Item](../msbuild/item-element-msbuild.md) 要素を含みます。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトで使用する各アイテムは、`ItemGroup` の子要素として指定する必要があります。  
  
## 構文  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`Condition`|省略可能な属性です。  評価する条件です。  詳細については、「[Conditions](../msbuild/msbuild-conditions.md)」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[項目](../msbuild/item-element-msbuild.md)|ビルド プロセスに対する入力項目を定義します。  `ItemGroup` には、`Item` 要素を 0 個以上指定できます。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[プロジェクト](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルの必須のルート要素です。|  
|[Target](../msbuild/target-element-msbuild.md)|.NET Framework 3.5 以降では、`ItemGroup` 要素を `Target` 要素内で使用できます。  詳細については、「[ターゲット](../msbuild/msbuild-targets.md)」を参照してください。|  
  
## 解説  
  
## 使用例  
 次のコード例は、1 つの `ItemGroup` 要素内に宣言されたユーザー定義のコレクション `Res` および `CodeFiles` を示しています。  各 `Res` アイテム コレクションの中には、ユーザー定義の [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) 子要素があります。  
  
```  
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
  
## 参照  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)   
 [Common MSBuild Project Items](../msbuild/common-msbuild-project-items.md)