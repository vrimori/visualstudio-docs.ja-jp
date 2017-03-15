---
title: "MSBuild エラー MSB3142 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyError"
helpviewer_keywords: 
  - "MSB3142"
ms.assetid: acca7437-6c72-446c-a6b5-a1c051b6855f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3142
**MSB3142: '\<ファイル\>' を '\<フォルダー\>' にコピーしようとしてエラーが発生しました: '\<エラー\>'**  
  
 このエラーは、setup.bin をビルド出力ディレクトリにコピーしようとしたときに生成されます。  このエラーでは以下の原因が考えられます。  
  
-   出力ディレクトリにコピーするアクセス許可が現在のユーザーにありません。  
  
-   ディスクの空き領域がありません。  
  
 これらは、file.copy または directory.createdirectory がエラーになる場合に考えられる原因と同じです。  
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)