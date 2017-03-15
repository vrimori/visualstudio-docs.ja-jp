---
title: "MSBuild エラー MSB3181 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateTargetPath"
helpviewer_keywords: 
  - "MSB3181"
ms.assetid: 49349fc2-3fa1-470d-a5cb-6ad72b93f408
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3181
**MSB3181: 2 つ以上のファイルに、同じターゲット パス '\<パス\>' が指定されています。**  
  
 この警告は、アプリケーション マニフェストの生成中に、複数の参照アセンブリまたはファイルのターゲット パスが同じ場合に生成されます。  パスにはファイル名が指定されているので、アセンブリどうしが配置時に上書きし合うことになります。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)