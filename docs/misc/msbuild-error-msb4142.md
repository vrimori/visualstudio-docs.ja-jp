---
title: "MSBuild エラー MSB4142 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4142"
ms.assetid: 56121c76-f952-43d1-ba23-1d1792fef0bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB4142
**MSB4142: MSBuildToolsPath が、ToolsVersion "\<x.x\>" の MSBuildBinPath と同じではありません。**  
  
 ツールセット定義で `MSBuildBinPath` と `MSBuildToolsPath` の値が異なります。  
  
### このエラーを解決するには  
  
-   ツールセット定義の `MSBuildBinPath` と `MSBuildToolsPath` が同じ値であることを確認します。  
  
## 参照  
 [標準ツールセット構成とカスタム ツールセット構成](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [追加のリソース](../msbuild/additional-msbuild-resources.md)