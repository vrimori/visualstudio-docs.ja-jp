---
title: "引数には Nothing を使用できません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrGeneral_ArgumentNullException"
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引数には Nothing を使用できません
値が必要な引数に null 値を指定しました。  
  
### このエラーを解決するには  
  
-   オブジェクトのインスタンスを作成していない状態で、オブジェクトの使用を試みた可能性があります。 そのような場合は、`New` キーワードを使用してインスタンスを作成します。  
  
-   値が正しく計算されることを確認してください。  
  
## 参照  
 [例外のトラブルシューティング : System.NullReferenceException](../Topic/Troubleshooting%20Exceptions:%20System.NullReferenceException.md)