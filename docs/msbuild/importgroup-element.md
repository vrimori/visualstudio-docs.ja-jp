---
title: "ImportGroup Element | Microsoft Docs"
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
  - "<ImportGroup> element [MSBuild]"
  - "ImportGroup element [MSBuild]"
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# ImportGroup Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

オプションの条件下でグループ化された `Import` 要素のコレクションが格納されます。  詳細については、「[Import 要素 \(MSBuild\)](../msbuild/import-element-msbuild.md)」を参照してください。  
  
## 構文  
  
```  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|`Condition`|省略可能な属性です。<br /><br /> 評価する条件です。  詳細については、「[Conditions](../msbuild/msbuild-conditions.md)」を参照してください。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[Import](../msbuild/import-element-msbuild.md)|あるプロジェクト ファイルから別のプロジェクト ファイルに内容をインポートします。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルの必須のルート要素です。|  
  
## 解説  
  
## 使用例  
 次のコード例は、`ImportGroup` 要素を示しています。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets) />  
        <Import Project="$(Targets2.targets) />  
    </ImportGroup>  
...  
</Project>  
```  
  
## 参照  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)