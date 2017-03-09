---
title: "コンパイラ エラー CS0629 | Microsoft Docs"
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
  - "CS0629"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0629"
ms.assetid: 20f22ef0-3c6f-4108-ab09-3f0752375a10
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0629
条件付きのメンバー 'member' は型 'Type Name' にインターフェイス メンバー 'base class member' を実装することはできません  
  
 [条件付き](http://msdn.microsoft.com/ja-jp/e1c4913b-74d0-421a-8a6d-c14b3f0e68fb)属性は、インターフェイスの実装で使用することはできません。  
  
 次の例では CS0629 が生成されます。  
  
```  
// CS0629.cs interface MyInterface { void MyMethod(); } public class MyClass : MyInterface { [System.Diagnostics.Conditional("debug")] public void MyMethod()    // CS0629, remove the Conditional attribute { } public static void Main() { } }  
```