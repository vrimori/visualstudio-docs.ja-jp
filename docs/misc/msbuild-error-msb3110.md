---
title: "MSBuild エラー MSB3110 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.IdentityFileNameMismatch"
helpviewer_keywords: 
  - "MSB3110"
ms.assetid: 58bf16bf-cf5b-4751-988d-c416952f216e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3110
**MSB3110: アセンブリ '\<assembly\>' には一致しない ID '\<AssemblyIdentity\>' があります。次のファイル名が必要です: '\<file\>'**  
  
 このエラーは、アセンブリ ID に基づいて取得したアセンブリ ファイル名が実際のファイル名と一致しない場合に生成されます。  
  
### このエラーを解決するには  
  
-   アセンブリ ファイル名を修正して、アセンブリ ID と対応するようにします。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)