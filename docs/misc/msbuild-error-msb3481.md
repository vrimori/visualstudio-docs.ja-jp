---
title: "MSBuild エラー MSB3481 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertNotInStore"
helpviewer_keywords: 
  - "MSB3481"
ms.assetid: 55f99775-3bd5-4e1b-b184-c6405d75e8ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3481
**MSB3481: 署名する証明書が見つかりませんでした。  現在のユーザーの個人用ストアであることを確認してください。**  
  
 このエラーは、署名証明書が個人用証明書ストアで見つからなかった場合に生成されます。  証明書が見つかったことを意味する [MSBuild エラー MSB3486](../misc/msbuild-error-msb3486.md) に似ていますが、このエラーは証明書が一致しないという意味です。  
  
### このエラーを解決するには  
  
-   プロジェクトの .pfx ファイルと一致する有効な証明書が個人用証明書ストアに存在することを確認します。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)