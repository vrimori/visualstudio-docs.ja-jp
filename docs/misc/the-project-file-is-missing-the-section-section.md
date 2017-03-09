---
title: "The project file is missing the &#39;section&#39; section | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_sectionerr"
ms.assetid: 516ab410-1b73-4539-9654-6323af6135b2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file is missing the &#39;section&#39; section
.vbproj ファイルまたは .csproj ファイルが破損しています。  次のいずれかのセクションがありません。  
  
-   Build  
  
-   \[ファイル\]  
  
-   VisualStudio  
  
-   VisualBasic または CSHARP  
  
 VisualStudio セクション、VisualBasic セクション、または CSHARP セクションが欠落している場合、プロジェクトは読み込まれません。  Build セクションまたは Files セクションが破損している場合、プロジェクト ファイルは次のように読み込まれます。  
  
-   Build が欠落している場合、すべてのビルド設定および構成情報は失われます。  
  
-   Files が欠落している場合、プロジェクトにはファイルが組み込まれません。  
  
 **このエラーを解決するには**  
  
-   プロジェクトを再作成します。  
  
## 参照  
 [プロジェクト ファイル](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)