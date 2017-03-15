---
title: "ItemMetadata Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemMetadata Element [MSBuild]"
  - "<ItemMetadata> Element [MSBuild]"
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# ItemMetadata Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ユーザー定義によるアイテム メタデータ キーを格納します。このキーにはアイテム メタデータ値を格納します。  1 つのアイテムは、メタデータ キーと値のペアを任意の数持つことができます。  
  
## 構文  
  
```  
<ItemMetadataName> Item Metadata value </ItemMetadataName>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|`Condition`|省略可能な属性です。<br /><br /> 評価する条件です。  詳細については、「[Conditions](../msbuild/msbuild-conditions.md)」を参照してください。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[項目](../msbuild/item-element-msbuild.md)|ビルド プロセスの入力を定義するユーザー定義の要素です。|  
  
## テキスト値  
 テキスト値は省略可能です。  
  
 アイテム メタデータの値を指定します。テキストまたは XML を指定できます。  
  
## 解説  
  
## 使用例  
 `Culture` メタデータに `fr` という値を設定して、アイテム `CSFile` に追加するコード例を次に示します。  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## 参照  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)