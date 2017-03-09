---
title: "コンパイラ エラー CS0721 | Microsoft Docs"
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
  - "CS0721"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0721"
ms.assetid: 7ab8591d-df8a-440c-80d6-61b438a935fd
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0721
'type': スタティック型をパラメーターとして使用することはできません  
  
 静的な型は、パラメーターとして意味がありません。 静的な型のインスタンスを作成できない場合があるため、インスタンスをパラメーターとして渡すことはできません。  
  
 次の例では CS0721 が生成されます。  
  
```  
// CS0721.cs public static class SC { } public class CMain { public void F(SC sc)  // CS0721 { } public static void Main() { } }  
```