---
title: "MSBuild エラー MSB3144 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.InvalidInput"
helpviewer_keywords: 
  - "MSB3144"
ms.assetid: 955e0db3-afe2-4c03-8e95-3419878374df
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3144
**MSB3144: ブートストラップを生成するために十分なデータが指定されませんでした。  'ApplicationFile' または 'BootstrapperItems' の少なくとも 1 つのパラメーターの値を指定してください。**  
  
 このエラーは、ブートストラップを生成するために十分なデータが指定されていない場合に発生します。  ビルド処理は、アプリケーション インストーラーもパッケージも含まれていない、空のブートストラップを作成します。  
  
### このエラーを解決するには  
  
-   `ApplicationFile` パラメーターまたは `BootstrapperItems` パラメーターの少なくともどちらかに値を指定します。  
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)