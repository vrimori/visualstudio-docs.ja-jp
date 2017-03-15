---
title: "MSBuild エラー MSB2006 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.UnrecognizedElement"
helpviewer_keywords: 
  - "MSB2006"
ms.assetid: 89dc1b89-1621-46bc-9fe6-6d98cbcbebc8
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB2006
**プロジェクト ファイルにはルート要素 \<{0}\> がありません。**  
  
 ルート要素名が正しく指定されていないか、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] が要素名を認識できません。  
  
### このエラーを解決するには  
  
-   要素名のスペルを確認します。  
  
-   プロジェクト ファイルに変更や破損がないことを確認します。  変更または破損がある場合は、プロジェクトを作成するのに使用したバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でプロジェクトをいったん開いて保存し直してから、再び変換してください。  
  
## 参照  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [追加のリソース](../msbuild/additional-msbuild-resources.md)