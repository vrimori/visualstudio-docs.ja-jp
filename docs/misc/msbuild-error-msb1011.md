---
title: "MSBuild エラー MSB1011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.AmbiguousProjectError"
helpviewer_keywords: 
  - "MSB1011"
ms.assetid: f3cb16e5-288c-4dba-941f-a0ed3bf92db7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB1011
**このフォルダーは 2 つ以上のプロジェクト ファイルまたはソリューション ファイルを含んでいるため、使用するプロジェクト ファイルまたはソリューション ファイルを指定してください。**  
  
 コマンド ラインにプロジェクト ファイルが指定されなかった場合、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は、現在の作業ディレクトリから拡張子が "proj" または "sln" のファイルを検索し、そのファイルを使用します。  現在の作業ディレクトリには、"proj" または "sln" という拡張子のファイルが複数存在します。  
  
### このエラーを解決するには  
  
1.  コマンド ラインの指定にプロジェクト ファイルの名前を含めます。  たとえば、「`msbuild`」ではなく、「`msbuild myapp.proj`」と入力します。  
  
## 参照  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)