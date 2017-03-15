---
title: "MSBuild エラー MSB3163 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidComponentsLocation"
helpviewer_keywords: 
  - "MSB3163"
ms.assetid: 35c5efbf-2fd7-478c-bb8e-3c4eabb3e4d4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3163
**MSB3163: ビルド入力パラメーター 'ComponentsLocation\='\<ComponentsLocation\>'' は無効です  値は、'HomeSite'、'Relative'、または 'Absolute' のうちの 1 つでなければなりません。  'HomeSite' を既定とします。**  
  
 このエラーは、`ComponentsLocation` プロパティ \(必要条件のインストール元となる場所\) に指定された値が無効の場合に発生します。  `ComponentsLocation` の値は、`HomeSite`、`Relative`、または `Absolute` のいずれかである必要があります。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)