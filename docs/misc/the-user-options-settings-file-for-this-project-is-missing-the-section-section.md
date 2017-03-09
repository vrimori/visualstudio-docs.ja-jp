---
title: "The user options settings file for this project is missing the &#39;section&#39; section | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.peruserfile_sectionerr"
ms.assetid: 576070f5-76b6-46e4-8aba-83442521027f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The user options settings file for this project is missing the &#39;section&#39; section
Build ノードが .vbproj.user または .csproj.user ファイルから欠落しています。  
  
 Build セクションにはデバッグの設定が含まれています。  このセクションが欠落していると、ユーザーのデバッグ設定は読み込まれず、既定の値が設定されます。  
  
 この状況は、プロジェクト ファイルを手動で編集した場合によく発生します。  
  
 プロジェクトの終了時に、プロジェクト システムにより、ユーザーごとのプロジェクト ファイルが自動的に再作成されます。  
  
 この警告は情報を提供するためのものです。  
  
## 参照  
 [プロジェクト ファイル](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)