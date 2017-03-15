---
title: "MSBuild エラー MSB3161 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CircularDependency"
helpviewer_keywords: 
  - "MSB3161"
ms.assetid: 2871d071-7c3a-4103-8b14-6ee56564a7f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3161
**MSB3161: 循環する依存関係が、次のビルドされたパッケージ間で検出されました: '\<パッケージ\>'**  
  
 この警告は、ブートストラップ パッケージの依存関係のグラフに循環依存関係が存在する場合に生成されます \(例 : A → B → C → A\)。  このような場合、ブートストラップは最初にインストールするパッケージを判断できません。  
  
### このエラーを解決するには  
  
-   循環依存関係を削除します。削除するには、ブートストラップ パッケージ ファイルに記述されている依存関係を変更するか、依存関係にあるパッケージのどれかのインストールをしないようにします。  
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)