---
title: "MSBuild エラー MSB4136 | Microsoft Docs"
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
  - "MSB4136"
ms.assetid: 6f0543d3-f8c0-44e1-8748-8a71be599bf4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB4136
**MSB4136: 構成ファイル \<ファイル名\> からツールセット情報を読み取り中にエラーが発生しました。**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] が [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 構成ファイル \(msbuild.exe.config\) のツールセット情報を読み取るときにエラーを受け取りました。  
  
### このエラーを解決するには  
  
-   構成ファイルが正しく、適切な形式であることを確認します。  たとえば、ツールセットを追加して .config ファイルをカスタマイズした場合は、ツールセットの定義をチェックしてください。  
  
## 参照  
 [ToolsVersion 設定のオーバーライド](../msbuild/overriding-toolsversion-settings.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [追加のリソース](../msbuild/additional-msbuild-resources.md)