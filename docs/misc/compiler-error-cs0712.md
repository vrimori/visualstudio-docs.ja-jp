---
title: "コンパイラ エラー CS0712 | Microsoft Docs"
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
  - "CS0712"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0712"
ms.assetid: cde64c0c-3953-4563-8c24-8b646230bbb8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0712
静的クラス 'static class' のインスタンスを作成することはできません。  
  
 静的クラスのインスタンスを作成することはできません。 静的クラスは、静的フィールドおよびメソッドを格納するよう設計されていますが、インスタンス化されないことがあります。  
  
## 使用例  
 次の例では CS0712 が生成されます。  
  
```  
// CS0712.cs public static class SC { } public class CMain { public static void Main() { SC sc = new SC();  // CS0712 } }  
```