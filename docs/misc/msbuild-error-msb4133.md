---
title: "MSBuild エラー MSB4133 | Microsoft Docs"
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
  - "MSB4133"
ms.assetid: 5f18937a-fda1-4315-81f9-7cee02802a6d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB4133
**MSB4133: 既定のツール バージョン "\<x.x.\>" が指定されましたが、その定義が見つかりませんでした。**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] がプロジェクト ファイルに `DefaultToolsVersion` として定義されたツールセットを見つけることができません。  
  
### このエラーを解決するには  
  
-   `DefaultToolsVersion` が正しく指定され、このツールセットがレジストリまたは [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 構成ファイルに定義されていることを確認してください。  
  
## 参照  
 <xref:Microsoft.Build.BuildEngine.Toolset>   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [追加のリソース](../msbuild/additional-msbuild-resources.md)