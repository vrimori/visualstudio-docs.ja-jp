---
title: "MSBuild エラー MSB3119 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionMissingLeadDot"
helpviewer_keywords: 
  - "MSB3119"
ms.assetid: 52d68b0e-01d4-436f-a96c-733fd20a8c04
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3119
**MSB3119: ファイルの関連付けの拡張子は、ピリオド \(.\) で始まっている必要があります。**  
  
 このエラーは、ファイルの関連付けを構成するときに拡張子がピリオド \(.\) で始まっていない場合に発生します。  
  
### このエラーを解決するには  
  
-   [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md) `extension` 属性をピリオド \(.\) で始まる値 \(".doc" など\) に設定します。  
  
## 参照  
 [\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)