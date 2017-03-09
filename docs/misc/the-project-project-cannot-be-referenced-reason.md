---
title: "The project &#39;project&#39; cannot be referenced. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_reference_project"
ms.assetid: 9a7c9283-64db-48af-a782-90322af83a74
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project &#39;project&#39; cannot be referenced. &lt;reason&gt;
特定のプロジェクトに対するプロジェクト対プロジェクトの参照が作成されていません。  
  
 このエラーの最も一般的な原因は、実行可能ファイル \(.EXE\) を構築するプロジェクトを参照していることです。  このエラーは、プロジェクトが、アセンブリ以外の出力を生成するプロジェクト \(ネイティブな C\+\+ アプリケーションなど\) を参照している可能性も示しています。  
  
## 参照  
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)