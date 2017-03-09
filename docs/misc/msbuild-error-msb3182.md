---
title: "MSBuild エラー MSB3182 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.TargetPathTooLong"
helpviewer_keywords: 
  - "MSB3182"
ms.assetid: b257a206-b12b-453b-97d8-2cb9a0d3dcc9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3182
**MSB3182: ファイル名 '\<ファイル\>' は '\<長さ\>' 文字を超えています。**  
  
 この警告は、`TargetPath` プロパティの値が長すぎる場合に生成されます。  これは、アプリケーション マニフェストと配置マニフェストのどちらも対象になります。  
  
### このエラーを解決するには  
  
-   `TargetPath` プロパティの値を編集して、短くします。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)