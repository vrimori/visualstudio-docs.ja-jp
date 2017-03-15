---
title: "MSBuild エラー MSB4132 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4132"
ms.assetid: 4ac265a7-0f8d-4fec-ba6e-cd70cbd5d89e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB4132
**MSB4132: ツール バージョン "'\<version\>'" が認識されません。**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] が `ToolsVersion` に指定された値に対応するツールセットを見つけました。  
  
### このエラーを解決するには  
  
-   `ToolsVersion` に、プロジェクト タグまたは MSBuild **\/ToolsVersion** スイッチを使用するときにコマンド ラインで有効な値を指定してください。  
  
## 参照  
 <xref:Microsoft.Build.Tasks.MSBuild.ToolsVersion%2A>   
 [追加のリソース](../msbuild/additional-msbuild-resources.md)