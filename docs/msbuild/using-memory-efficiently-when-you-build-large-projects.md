---
title: "大規模なプロジェクトのビルドにおけるメモリの効率的な使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "キャッシュ (MSBuild)"
  - "メモリの使用量 (MSBuild)"
  - "msbuild, 効率的なメモリ使用 (大規模なプロジェクトのビルド)"
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 大規模なプロジェクトのビルドにおけるメモリの効率的な使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

大規模なプロジェクトには多数のサブプロジェクトやその他の依存関係が含まれていることが多く、それらがビルド時に大量のシステム メモリを消費することがあります。  システム メモリの容量が減少すると、システム パフォーマンスも低下するおそれがあります。  古いバージョンの [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトはメモリに残されていました。Version 3.5 では、プロジェクトが削除されるようになりましたが、ビルド結果は後で取得できるようにキャッシュに保持されていました。  
  
 Version 4.0 では、このメモリ管理が自動的に処理されるため、プロジェクトで `UnloadProjectsOnCompletion` や `UseResultsCache` などのプロパティを使用する必要はありません。  
  
## 参照  
 [複数のプロジェクトの並行ビルド](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)