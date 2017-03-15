---
title: "MSBuild エラー MSB3113 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ResolveFailedInReadWriteMode"
helpviewer_keywords: 
  - "MSB3113"
ms.assetid: 81e73738-e6ee-4651-9f48-acb1feef3ff5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3113
**MSB3113: ファイル '\<ファイル\>' が見つかりませんでした。**  
  
 このエラーは、新しいマニフェストの作成中に解決できない参照が検出された場合に生成されます。  原因は、プロジェクト ファイルまたはタスク パラメーターにある可能性があります。  
  
### このエラーを解決するには  
  
-   プロジェクト ファイル \(および、カスタム ビルド中の場合はビルド パラメーター\) にファイル参照の競合がないかどうかを確認します。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)