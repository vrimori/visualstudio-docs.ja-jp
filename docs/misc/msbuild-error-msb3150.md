---
title: "MSBuild エラー MSB3150 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
helpviewer_keywords: 
  - "MSB3150"
ms.assetid: 90d86aef-f4df-4070-8ecc-173eb40668aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3150
**MSB3150: ブートストラップをカルチャ '{0}' でビルドするために利用可能な文字列リソースがありません。**  
  
 このエラーは、見つかった setup.xml に文字列ノードが含まれていない場合に発生します。  XML ファイルが壊れている可能性があります。  
  
### このエラーを解決するには  
  
-   **\[コントロール パネル\]** の **\[プログラムの追加と削除\]** を選択し、Visual Studio SDK を修復するか、必要なファイルを適切なディレクトリ \(\<SDK install path\>\\bootstrapper\\engine\\\<culture\>\\setup.xml\) にコピーします。