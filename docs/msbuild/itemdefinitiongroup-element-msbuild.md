---
title: "ItemDefinitionGroup Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemDefinitionGroup Element [MSBuild]"
  - "<ItemDefinitionGroup> Element [MSBuild]"
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# ItemDefinitionGroup Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`ItemDefinitionGroup` 要素では、既定でプロジェクト内のすべての項目に適用されるメタデータ値である一連の項目定義を定義できます。  ItemDefinitionGroup は、[CreateItem Task](../msbuild/createitem-task.md)および [CreateProperty Task](../msbuild/createproperty-task.md)よりも優先されます。  詳細については、「[項目定義](../msbuild/item-definitions.md)」を参照してください。  
  
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
  
|属性|Description|  
|--------|-----------------|  
|`Condition`|省略可能な属性です。  評価する条件です。  詳細については、「[Conditions](../msbuild/msbuild-conditions.md)」を参照してください。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[項目](../msbuild/item-element-msbuild.md)|ビルド プロセスに対する入力項目を定義します。  `ItemDefinitionGroup` には、`Item` 要素を 0 個以上指定できます。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルの必須のルート要素です。|  
  
## 使用例  
 次のコード例では、m と n という 2 つのメタデータ項目を ItemDefinitionGroup に定義します。  この例では、項目 "i" ではメタデータ "m" が明示的に定義されていないため、既定のメタデータ "m" が項目 "i" に適用されます。  ただし、項目 "i" でメタデータ "n" が既に定義されているため、既定のメタデータ "n" は項目 "i" には適用されません。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  
  
## 参照  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)