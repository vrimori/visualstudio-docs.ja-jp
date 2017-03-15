---
title: "MSBuild エラー MSB3486 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertificateError"
helpviewer_keywords: 
  - "MSB3486"
ms.assetid: 75d03d8e-3a28-4010-b602-61fe037dec74
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3486
**MSB3486: ストア '{証明書ストア}' から証明書を取得できません。**  
  
 このエラーは、プロジェクトの .pfx ファイルの拇印と一致する証明書が個人用証明書ストアで見つからない場合に、`ResolveKeySource` MSBuild タスクから発生します。  
  
### このエラーを解決するには  
  
-   プロジェクトの .pfx ファイルの拇印が個人用証明書ストアの証明書の拇印と一致することを確認します。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)