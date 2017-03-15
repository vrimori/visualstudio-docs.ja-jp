---
title: "MSBuild エラー MSB3176 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.GreaterMinimumRequiredVersion"
helpviewer_keywords: 
  - "MSB3176"
ms.assetid: 9138f5ce-4af6-428e-8ac4-c4390a154daf
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3176
**MSB3176: 必要なバージョンとして指定されているバージョンは、現在の発行するバージョンより新しいものです。  現在の発行するバージョンと同じか、またはそれよりも古いバージョンを指定してください。**  
  
 このエラーは、最低限必要なアプリケーション バージョンが配置マニフェストの現在のバージョンより新しい場合に生成されます。  
  
### このエラーを解決するには  
  
-   最低限必要なバージョンに、現在の発行するバージョンと同じか、それよりも古いバージョンを指定します。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)