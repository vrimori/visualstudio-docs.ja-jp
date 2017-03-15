---
title: "MSBuild エラー MSB3146 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.MissingDependency"
helpviewer_keywords: 
  - "MSB3146"
ms.assetid: 717fd649-3024-427d-a068-cff8034ffc0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3146
**MSB3146: 項目 '\<パッケージ\>' は '\<パッケージ\>' で必要ですが、含まれていませんでした。**  
  
 このエラーは、別のブートストラップに依存しているブートストラップがあるにもかかわらず、依存している側のブートストラップだけインストールした場合に発生します。  たとえば、パッケージ B がパッケージ A に依存しているのに、B だけインストールされている場合です。  
  
### このエラーを解決するには  
  
-   必要なパッケージを含めます。