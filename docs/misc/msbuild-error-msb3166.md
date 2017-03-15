---
title: "MSBuild エラー MSB3166 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageResourceFileNotFound"
  - "vsdeploy.chm:13166"
helpviewer_keywords: 
  - "MSB3166"
ms.assetid: f5dff83a-1e41-4c92-a137-89b7e9f3cd93
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3166
**MSB3166: 項目 '\<パッケージ\>' に対する必要なファイル '{0}' が見つかりませんでした。**  
  
 このエラーは、使用許諾契約書 \(EULA: End\-User License Agreement\) または外部チェック ファイルがない場合に生成されます。  このファイルがディスク上に存在することを確認します。  
  
### このエラーを解決するには  
  
-   Visual Studio SDK をインストールし直します。  
  
     または  
  
-   必要なファイルを適切な場所にコピーします。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)