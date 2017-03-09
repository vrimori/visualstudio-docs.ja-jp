---
title: "MSBuild エラー MSB3128 | Microsoft Docs"
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
  - "GenerateManifest.ManifestsSignedHashExcluded"
helpviewer_keywords: 
  - "MSB3128"
ms.assetid: e8612a4b-4016-48d2-b5f0-a1091bfe8cb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3128
**MSB3128: ClickOnce マニフェストにはハッシュされていない参照が含まれているため、署名できません。**  
  
 署名付きマニフェストのあるアプリケーションを発行する場合、すべてのファイルはハッシュに含まれている必要があります。  
  
### このエラーを解決するには  
  
1.  **プロジェクト デザイナー**の **\[発行\]** ページに移動します。  
  
2.  **\[アプリケーション ファイル\]** をクリックします。  
  
3.  発行するすべてのファイルについて、**\[ハッシュ\]** 値を **\[含む\]** に設定します。  
  
## 参照  
 [\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)