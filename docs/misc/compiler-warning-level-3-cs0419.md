---
title: "コンパイラの警告 (レベル 3) CS0419 | Microsoft Docs"
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
  - "CS0419"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0419"
ms.assetid: de439ad5-422f-4ed6-96d6-69dade29c7b2
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 3) CS0419
Cref 属性の参照があいまいです: 'Method Name1'。  'Method Name2' を仮定しますが、'Method Name3' を含む別のオーバーロードに一致した可能性もあります。  
  
 コード内の XML ドキュメント コメントで、参照を解決できませんでした。 このエラーは、メソッドがオーバーロードされている場合や、同じ名前に 2 つの異なる識別子が見つかった場合に発生することがあります。 警告を解決するには、修飾名を使用して参照を明確にするか、特定のオーバーロードをかっこで囲みます。  
  
 次の例では CS0419 が生成されます。  
  
```  
// cs0419.cs // compile with: /doc:x.xml /W:3 interface I { /// text for F(void) void F(); /// text for F(int) void F(int i); } /// text for class MyClass public class MyClass { /// <see cref="I.F"/> public static void MyMethod(int i) { } /* Try this instead: /// <see cref="I.F(int)"/> public static void MyMethod(int i) { } */ /// text for Main public static void Main () { } }  
```