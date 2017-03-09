---
title: "MSBuild エラー MSB3165 | Microsoft Docs"
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
  - "vsdeploy.chm:13165"
  - "MSBuild.GenerateBootstrapper.DifferingPublicKeys"
helpviewer_keywords: 
  - "MSB3165"
ms.assetid: 2f50462e-947d-4211-b197-e58eddcfd373
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3165
**MSB3165: '\<パッケージ\>' 内の '\<パブリック キー\> 属性の値はファイル '\<ファイル\>' の値と一致しません。**  
  
 この警告は、ブートストラップ パッケージ ファイルに指定された公開キーが、ディスク上の再頒布可能パッケージの署名と一致しない場合、または再頒布可能パッケージが署名されていない場合に発生します。  ビルドは、ディスク上の再頒布可能パッケージが署名されている場合はその公開キーの値を使用し、署名されていない場合はそのハッシュを使用します。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)