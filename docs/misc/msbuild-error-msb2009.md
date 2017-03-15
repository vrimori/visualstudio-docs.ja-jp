---
title: "MSBuild エラー MSB2009 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedAttribute"
helpviewer_keywords: 
  - "MSB2009"
ms.assetid: 34fd83b4-dead-49e5-b1ee-b23dc5a95244
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB2009
**'\<要素名\>' 要素の '\<属性名\>' 属性が無効です。**  
  
 属性名が正しく指定されていないか、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] が属性名を認識できません。  
  
### このエラーを解決するには  
  
-   属性名のスペルを確認します。  
  
-   プロジェクト ファイルに変更や破損がないことを確認します。  変更または破損がある場合は、プロジェクトを作成するのに使用したバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でプロジェクトをいったん開いて保存し直してから、再び変換してください。  
  
## 参照  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)