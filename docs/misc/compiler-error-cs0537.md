---
title: "コンパイラ エラー CS0537 | Microsoft Docs"
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
  - "CS0537"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0537"
ms.assetid: 6c832a5f-47dc-4f60-aed8-69ac328af44b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0537
クラス System.Object は基底クラスを含んだり、インターフェイスを実装したりできません。  
  
 CS0537 は、<xref:System> クラス ライブラリをリビルドするときに、<xref:System.Object> が別のクラスから派生する場合に発生します。 このエラーが発生することはめったにありません。 発生した場合は、<xref:System.Object> をクラスまたはインターフェイスから派生させないでください。これは .NET Framework クラス階層全体のルートであり、他のものから派生しません。