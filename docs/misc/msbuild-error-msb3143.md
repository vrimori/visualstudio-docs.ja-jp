---
title: "MSBuild エラー MSB3143 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyPackageError"
helpviewer_keywords: 
  - "MSB3143"
ms.assetid: b4278c8c-31df-4b4f-9ef9-7b9327e8ee77
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3143
**MSB3143: 項目 '\<パッケージ\>' の '\<ファイル\>' をコピーしようとしてエラーが発生しました: '\<エラー\>'**  
  
 このエラーは、ブートストラップ パッケージがビルド出力ディレクトリにコピーされたときに発生します。  このエラーでは以下の原因が考えられます。  
  
-   ビルド出力ディレクトリにコピーするアクセス許可が現在のユーザーにありません。  
  
-   ディスクの空き領域がありません。  
  
 これらは、file.copy または directory.createdirectory がエラーになる場合に考えられる原因と同じです。  
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)