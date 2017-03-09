---
title: "コンパイラ エラー CS0505 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0505"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0505"
ms.assetid: e3cb9e33-7338-4869-859b-81d7439f0d23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0505
'member1': 'member2' は関数ではないためオーバーライドできません  
  
 クラス宣言で、基底クラスのメソッド以外のものをオーバーライドしようとしました。 オーバーライドでは、メンバーの型が一致しなければなりません。 基底クラスのメソッドと同じ名前のメソッドが必要な場合、基底クラスのメソッド宣言で [new](/dotnet/csharp/language-reference/keywords/new) をご使用ください \([override](/dotnet/csharp/language-reference/keywords/override) は使用しない\)。  
  
 次の例では CS0505 が生成されます。  
  
```  
// CS0505.cs // compile with: /target:library public class clx { public int i; } public class cly : clx { public override int i() { return 0; }   // CS0505 }  
```