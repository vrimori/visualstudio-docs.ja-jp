---
title: "The parent file, &#39;file1&#39;, for file &#39;file2&#39; cannot be found in the project file | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_missing_dependency"
ms.assetid: 1902c0b5-d09d-49b9-8f71-e325f7b9cfd7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The parent file, &#39;file1&#39;, for file &#39;file2&#39; cannot be found in the project file
プロジェクト システムが、ファイルに対応するノードを見つけることができません。  
  
 依存ファイルは、`<File>` ノードに `DependentUpon` 属性を追加することにより、プロジェクト ファイルに永続化できます。  次に例を示します。  
  
```  
<File  
    RelPath = "Form1.resx"  
    SubType = "Code"  
    BuildAction = "EmbeddedResource"  
    DependentUpon="Form1.vb"  
/>  
```  
  
 これにより、Form1.resx が、プロジェクト階層で Form1.vb の下に表示されます。  
  
 このエラーの原因として最も可能性が高いのは、プロジェクト ファイルを手動で編集したことです。  
  
### このエラーを解決するには  
  
-   プロジェクト ファイルを編集し、更新します。  
  
     影響を受けたファイルはプロジェクトに追加されますが、依存関係は保持されません。  
  
## 参照  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)