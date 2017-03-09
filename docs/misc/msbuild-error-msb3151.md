---
title: "MSBuild エラー MSB3151 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
helpviewer_keywords: 
  - "MSB3151"
ms.assetid: e4766734-2e90-436e-850b-a8a9da535dee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3151
**MSB3151: 項目 '\<パッケージ\>' は既に '\<パッケージ\>' を含んでいます。**  
  
 この警告は、ブートストラップ パッケージを 2 つ選択したときに、一方のパッケージが他方に含まれている場合に発生します。たとえば、含まれているパッケージが重複している場合です。  
  
### このエラーを解決するには  
  
-   余分に含まれているパッケージのチェック ボックスをオフにします。