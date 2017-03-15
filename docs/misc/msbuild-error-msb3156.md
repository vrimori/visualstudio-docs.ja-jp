---
title: "MSBuild エラー MSB3156 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductValidation"
helpviewer_keywords: 
  - "MSB3156"
ms.assetid: 98b1bd42-9efe-44a2-8a43-476edc03590d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3156
**MSB3156: '\<フォルダー\>' にある項目 '\<パッケージ\>' は XML 検証をパスしませんでした。**  
  
 この警告は、マニフェスト \(具体的には product.xml\) が XML 検証にパスしなかった場合に生成されます。  問題の詳細は、後続のエラー メッセージ \([MSBuild エラー MSB3159](/visual-cpp/misc/msbuild-error-msb3159) または [MSBuild エラー MSB3160](../misc/msbuild-error-msb3160.md)\) に示されます。  
  
### このエラーを解決するには  
  
-   後続のエラー メッセージに示された、マニフェストの検証に関する問題を解決します。  
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)