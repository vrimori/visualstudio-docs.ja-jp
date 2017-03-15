---
title: "MSBuild エラー MSB3188 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PrerequisiteNotSigned"
helpviewer_keywords: 
  - "MSB3188"
ms.assetid: 8520e960-3b31-4e25-9fce-b9092b869bd0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3188
**MSB3188: アセンブリ '\<アセンブリ\>' は、必要条件として設定されるためには、厳密に署名されていなければなりません。**  
  
 このエラーは、必要条件であるアセンブリが厳密に署名されていない場合に生成されます。  このエラーは、アプリケーション マニフェストについてのみ発生します。  
  
### このエラーを解決するには  
  
-   プロジェクトで使用するすべてのアセンブリが厳密に署名されていることを確認します。