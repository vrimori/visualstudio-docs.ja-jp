---
title: "コンパイラ エラー CS0720 | Microsoft Docs"
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
  - "CS0720"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0720"
ms.assetid: 1a8e7613-6bfb-4178-a8b4-f4591316c0b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0720
'static class': 静的クラスでインデクサーを宣言することはできません  
  
 インデクサーは静的クラスでは無意味です。インデクサーはインスタンスでのみ使用でき、静的な型のインスタンスを作成することはできません。  
  
## 使用例  
 次の例では CS0720 が生成されます。  
  
```  
// CS0720.cs public static class Test { public int this[int index]  // CS0720 { get { return 1; } set {} } static void Main() {} }  
```