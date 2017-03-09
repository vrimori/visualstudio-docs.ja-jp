---
title: "MSBuild エラー MSB3120 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionTooLong"
helpviewer_keywords: 
  - "MSB3120"
ms.assetid: 20bc64f5-aadc-4eec-9915-a87a3d7f81ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3120
**MSB3120: ファイルの関連付けの拡張子 '\<extension\>' が、許可されている最大長 \<maximumlength\> を超えています。**  
  
 ファイルの関連付けの拡張子の文字数は、指定された値を超えることはできません。  
  
### このエラーを解決するには  
  
-   [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md) `extension` 属性を、対象のオペレーティング システムで許可される制限を超えない文字数の値に設定します。  
  
## 参照  
 [\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)