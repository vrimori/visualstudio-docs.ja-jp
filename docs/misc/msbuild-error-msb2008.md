---
title: "MSBuild エラー MSB2008 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedChildElement"
helpviewer_keywords: 
  - "MSB2008"
ms.assetid: 3c2afda0-a116-4b2f-af0c-c0f0d1541325
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB2008
**Visual Studio プロジェクト システムでは、"{0}" プロジェクトを変換できません。  C\# および VB クライアント プロジェクト以外は、このシステムを使って変換できません。**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] を使用して変換できるのは、有効な [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] および [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] プロジェクトだけです。  
  
### このエラーを解決するには  
  
-   [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] または [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] プロジェクトの場合は、そのプロジェクト ファイルに変更または破損がないかどうかを確認してください。  変更または破損がある場合は、プロジェクトを作成するのに使用したバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でプロジェクトをいったん開いて保存し直してから、再び変換してください。  
  
-   [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] または [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] プロジェクトでない場合は、適切なツールを使って変換してください。  
  
## 参照  
 [追加のリソース](../msbuild/additional-msbuild-resources.md)