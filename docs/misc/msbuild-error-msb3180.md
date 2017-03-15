---
title: "MSBuild エラー MSB3180 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateComDefinition"
helpviewer_keywords: 
  - "MSB3180"
ms.assetid: 98d8cb76-6176-4121-82ee-8a297d9deebc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3180
**MSB3180: COM コンポーネント '\<アセンブリ\>' は、'\<ファイル\>' および '\<ファイル\>' で clsid\/tlbid\="'\<アセンブリ\>'" に定義されています。**  
  
 このエラーは、ファイル参照または依存マニフェストで \(クラスまたはタイプ ライブラリへの\) COM 参照の重複が見つかった場合に、アプリケーション マニフェスト生成プロセスで生成されます。  
  
 たとえば、外部マニフェストを持つ COM オブジェクトへの参照、および内部マニフェストを持つ同じ COM オブジェクトへの参照を追加した場合、このエラーが表示される可能性があります。  
  
### このエラーを解決するには  
  
-   重複している COM 参照の一方を削除します。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)