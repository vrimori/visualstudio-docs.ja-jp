---
title: "MSBuild エラー MSB3124 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsDuplicateExtensions"
helpviewer_keywords: 
  - "MSB3124"
ms.assetid: d8365103-aa9d-400e-9c24-0a43e2bfbd14
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3124
**MSB3124: 拡張子 '\<extensionname\>' のファイルの関連付けは既に作成されています。**  
  
 このエラーは、ファイルの関連付け拡張子が重複する場合に発生します。  
  
### このエラーを解決するには  
  
-   一意でない [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md) `extension` 属性を削除します。  示される各 \<fileAssociation\> 要素の拡張子属性は、一意である必要があります。  
  
## 参照  
 [\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)