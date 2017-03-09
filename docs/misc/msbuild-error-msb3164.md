---
title: "MSBuild エラー MSB3164 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageHomeSiteMissing"
helpviewer_keywords: 
  - "MSB3164"
ms.assetid: 5a1e31fc-0322-4d4e-8c26-013b1efb82c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3164
**MSB3164: '\<パッケージ\> に対して 'HomeSite' 属性が指定されていませんでした。そのため、パッケージは同じ場所にブートストラップとして発行されます。**  
  
 この警告は、ユーザーが HomeSite を使用しようとしたときに、指定されたパッケージに関する適切な HomeSite 情報がなかった場合に生成されます。  
  
### このエラーを解決するには  
  
-   マニフェスト ファイルを更新して、HomeSite 情報を追加します。  
  
-   または、HomeSite を使用しないようにします。  
  
## 参照  
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)