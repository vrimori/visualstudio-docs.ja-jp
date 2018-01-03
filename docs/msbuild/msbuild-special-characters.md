---
title: "MSBuild の特殊文字 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9859cf55b3b9fd4745c5e799a9a54e7c1d2cb9cd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-special-characters"></a>MSBuild の特殊文字
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] では、特定の文脈で特別な使い方をするためにいくつかの文字が予約されています。 予約されている文脈でそのような文字を文字通り使用するには、エスケープする必要があります。 たとえば、アスタリスクは、項目定義の `Include` 属性と `Exclude` 属性、ならびに `CreateItem` の呼び出しで特別な意味を持ちます。 このような文脈でアスタリスクをアスタリスクとして表示するには、エスケープする必要があります。 その他の文脈では、アスタリスクを使う場所でそれを入力できます。  
  
 特殊文字をエスケープするには、構文 %*xx* を使用します。*xx* は、文字の ASCII 16 進数値を表します。 詳しくは、「[方法 : MSBuild で特殊文字をエスケープする](../msbuild/how-to-escape-special-characters-in-msbuild.md)」をご覧ください。  
  
## <a name="special-characters"></a>特殊文字  
 次の表は、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] の特殊文字をまとめたものです。  
  
|**文字**|**ASCII**|**予約されている使用方法**|  
|-------------------|---------------|------------------------|  
|%|%25|メタデータを参照する|  
|$|%24|プロパティを参照する|  
|@|%40|項目一覧を参照する|  
|'|%27|条件とその他の式|  
|;|%3B|一覧の区切り記号|  
|?|%3F|`Include` 属性と `Exclude` 属性のファイル名のワイルドカード文字|  
|*|%2A|`Include` 属性と `Exclude` 属性のファイル名で使用するワイルドカード文字|  
  
## <a name="see-also"></a>参照  
 [詳細な概念](../msbuild/msbuild-advanced-concepts.md)   
 [項目](../msbuild/msbuild-items.md)