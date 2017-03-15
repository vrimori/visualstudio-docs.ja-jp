---
title: "例外のトラブルシューティング : System.Reflection.TargetException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Reflection.TargetException 例外"
  - "TargetException 例外"
ms.assetid: 88b8e4b4-f1a3-4c4a-b1ef-cac176160803
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Reflection.TargetException
この例外は、無効な対象を呼び出そうとした場合にスローされます。  
  
## コメント  
 <xref:System.Reflection.TargetException> は、null オブジェクトで静的ではないメソッドを呼び出そうとしたときにスローされます。 たとえば、呼び出し元にメンバーへのアクセス権がないとき、対象でそのメンバーが定義されていないときなどの状況で発生します。  
  
## 参照  
 <xref:System.Reflection.TargetException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)