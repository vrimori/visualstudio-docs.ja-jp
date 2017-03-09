---
title: "MSBuild エラー MSB3157 | Microsoft Docs"
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
  - "vsdeploy.chm:13157"
  - "MSBuild.GenerateBootstrapper.UsingProductCulture"
helpviewer_keywords: 
  - "MSB3157"
ms.assetid: ccfcbea4-eb9b-42ae-9908-47079ecc84a7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3157
**MSB3157: カルチャ '\<カルチャ\>' を項目 '\<パッケージ\>' に対して一致できませんでした。  カルチャ '\<カルチャ\>' を使用します。**  
  
 この警告は、指定した製品が、指定したカルチャを使用するパッケージ マニフェスト ファイル \(package.xml\) を見つけられない場合に生成されます。  
  
### このエラーを解決するには  
  
-   適切なパッケージ マニフェスト ファイルを提供します。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)