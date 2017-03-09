---
title: "MSBuild エラー MSB3175 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidItemValue"
helpviewer_keywords: 
  - "MSB3175"
ms.assetid: c157e934-e4e6-43d9-abdf-cb4fb03be494
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3175
**MSB3175: 項目 '\<ビルドタスク\>' の '\<ファイル\>' の値は無効です。**  
  
 この警告は、`AssemblyType`、`DependencyType`、`FileType`、`TargetZone` などの列挙体ベースの各種タスク項目プロパティの値を、ビルド処理が認識できなかった場合に生成されます。  アプリケーション マニフェストと配置マニフェストのどちらも対象になります。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)