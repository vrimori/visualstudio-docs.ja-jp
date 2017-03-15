---
title: "MSBuild エラー MSB3184 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidInputManifest"
helpviewer_keywords: 
  - "MSB3184"
ms.assetid: 2be9f8e9-04ee-4299-b79f-965ee57a1a34
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3184
**MSB3184: 入力マニフェストが無効です。**  
  
 このエラーは、ビルド処理が、アプリケーション マニフェストか配置マニフェストが含まれていると想定してファイルを読み込んだところ、実際には別の内容 \(その他のマニフェストや壊れたデータなど\) が含まれていた場合に生成されます。  
  
### このエラーを解決するには  
  
-   プロジェクトのマニフェストが有効かつ適切であることを確認します。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)