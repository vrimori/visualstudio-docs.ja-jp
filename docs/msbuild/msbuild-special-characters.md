---
title: "MSBuild の特殊文字 | Microsoft Docs"
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
  - "エスケープ"
  - "エスケープ文字"
  - "MSBuild エスケープ文字"
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild の特殊文字
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] では、特定のコンテキストでの使用を目的として、いくつかの文字が予約されています。  そうした予約文字は、予約されているコンテキストでリテラル文字として使用する場合のみエスケープします。  たとえば、アスタリスクは項目定義の `Include` 属性と `Exclude` 属性、および `CreateItem` の呼び出しでのみ特別な意味を持ちます。  これらのコンテキストでアスタリスクをアスタリスクとして使用する場合は、エスケープする必要があります。  これらのコンテキスト以外では、アスタリスクをエスケープせずに記述できます。  
  
 特殊文字をエスケープするには、%*xx* という構文を使用します。*xx* は文字の ASCII 16 進値を表します。  詳細については、「[方法 : MSBuild で特殊文字をエスケープする](../msbuild/how-to-escape-special-characters-in-msbuild.md)」を参照してください。  
  
## 特殊文字  
 次の表は、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] の特殊文字の一覧です。  
  
|**文字**|**ASCII 文字。**|**予約の目的**|  
|------------|-------------------|---------------|  
|%|%25|メタデータの参照|  
|$|%24|プロパティの参照|  
|@|%40|項目リストの参照|  
|'|%27|条件およびその他の式|  
|;|%3B|リストの区切り記号|  
|?|%3F|`Include` 属性および `Exclude` 属性でファイル名に使用するワイルドカード文字|  
|\*|%2A|`Include` 属性および `Exclude` 属性でファイル名に使用するワイルドカード文字|  
  
## 参照  
 [詳細な概念](../msbuild/msbuild-advanced-concepts.md)   
 [項目](../msbuild/msbuild-items.md)