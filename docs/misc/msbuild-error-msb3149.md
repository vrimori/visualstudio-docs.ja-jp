---
title: "MSBuild エラー MSB3149 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoResources"
helpviewer_keywords: 
  - "MSB3149"
ms.assetid: 63857405-d420-457d-9ba7-80e1a2a9dcb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3149
**MSB3149: ブートストラップをビルドするために利用可能なリソースがありません。**  
  
 このエラーは、いずれかのカルチャに一致するブートストラップ リソース ファイル \(setup.xml\) が見つからなかった場合に発生します。  
  
### このエラーを解決するには  
  
-   **\[コントロール パネル\]** の **\[プログラムの追加と削除\]** を選択し、Visual Studio SDK を修復するか、必要なファイルを適切なディレクトリ \(\<SDK install path\>\\bootstrapper\\engine\\\<culture\>\\setup.xml\) にコピーします。  
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)