---
title: "コンパイラ エラー CS0619 | Microsoft Docs"
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
  - "CS0619"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0619"
ms.assetid: a2060eb1-cda5-493c-b049-9b1792f88207
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0619
'member' は使用されなくなりました: 'text'  
  
 クラス メンバーは [Obsolete](http://msdn.microsoft.com/ja-jp/05e99cd0-bda6-4f79-a890-1ca093b4b488) 属性でマークされているため、クラス メンバーが参照されるときにエラーが発行されます。  
  
 次の例では CS0619 が生成されます。  
  
```  
// CS0619.cs using System; public class C { [Obsolete("Use newMethod instead", true)]   // generates an error on use public static void m() { } // this is the method you should be using public static void newMethod() { } } class MyClass { public static void Main() { C.m();   // CS0619 } }  
```