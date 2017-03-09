---
title: "MSBuild エラー MSB3141 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.MissingVerificationInformation"
  - "vsdeploy.chm:13141"
helpviewer_keywords: 
  - "MSB3141"
ms.assetid: f32ce5fd-bb82-4a8b-aebe-61efef89cdc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3141
**MSB3141: 'PublicKey' または 'Hash' 属性が、項目 '\<パッケージ\>' のファイル '\<ファイル\>' に対して指定されていません。"**  
  
 このエラーは、ブートストラップ パッケージで HomeSite を使用しようとした場合に発生します。  ブートストラップ マニフェストに、実行時のファイル検証に使用する正しい情報 \(公開キーまたはハッシュ\) が含まれていません。  
  
### このエラーを解決するには  
  
-   情報が欠落しているパッケージ ファイルをダウンロードし、それをブートストラップ キャッシュにコピーします。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)