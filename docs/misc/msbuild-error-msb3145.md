---
title: "MSBuild エラー MSB3145 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidUrl"
helpviewer_keywords: 
  - "MSB3145"
ms.assetid: 183d4e7e-bdc6-402f-a1b6-531505be605f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3145
**MSB3145: ビルド入力パラメーター '\<プロパティ\>\=\<値\>' は Web URL または UNC 共有ではありません。**  
  
 このエラーは、`SupportUrl`、`ComponentsUrl`、および `ApplicationUrl` の各プロジェクト プロパティのいずれかの値が無効な場合に発生します。  値は有効な URI パスまたは UNC パスである必要があります。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)