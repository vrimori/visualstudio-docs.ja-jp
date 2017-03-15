---
title: "ファイル &#39;file&#39; をプロジェクトに追加できませんでした。 &lt;理由&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_file"
ms.assetid: 8bd70556-596a-4e24-a71c-a340604ee93d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# ファイル &#39;file&#39; をプロジェクトに追加できませんでした。 &lt;理由&gt;
.vbproj ファイルまたは .csproj ファイルから読み取られたファイルをプロジェクトに追加できません。 原因は次のとおりです。  
  
-   ファイル名が正しくない。  
  
-   ファイルがパスに満たない。 たとえば、プロジェクトの相対パスとして "File1\\File2.txt" があるときに、"File1\\File2.txt" という相対パスのフォルダーも存在する場合があります。  
  
-   項目が既に存在している。 これは、ファイルがプロジェクト ファイルに重複してリストされている場合に発生します。  
  
-   リンクが既に存在している。[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] および [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] のプロジェクト システムの制限により、同じ名前のリンクはプロジェクトごとに 1 つしか存在できません。 つまり、プロジェクトには、たとえばフォルダー A およびフォルダー B の両方に存在する file.vb というファイルへのリンクは作成できません。  
  
 このエラーの原因として最も可能性が高いのは、プロジェクト ファイルを手動で編集したことです。  
  
 この診断が表示されるファイルは、プロジェクトに追加されません。  
  
## 参照  
 [プロジェクト ファイル](/visual-cpp/ide/project-files)   
 [NIB: プロジェクトにおける項目の管理](http://msdn.microsoft.com/ja-jp/762e606b-7f44-4b66-97a1-e30a703654a0)