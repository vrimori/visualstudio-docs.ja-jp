---
title: "MSBuild エラー MSB3148 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoOutputPath"
helpviewer_keywords: 
  - "MSB3148"
ms.assetid: 389b335f-5760-4dcc-9146-c52d6d7ac81f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3148
**MSB3148: 出力パスがビルド設定で指定されていません。**  
  
 このエラーは、出力パスの指定が null または無効の場合に発生します。たとえば、プロジェクト ファイル内で `OutputPath=""` と指定されている場合です。  出力パスの既定値は `CurrentDirectory` です。  
  
### このエラーを解決するには  
  
-   `OutputPath` が空白でないか、プロジェクト ファイル内に指定されていないことを確認します。  
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)