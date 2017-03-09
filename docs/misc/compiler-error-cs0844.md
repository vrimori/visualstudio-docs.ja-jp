---
title: "コンパイラ エラー CS0844 | Microsoft Docs"
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
  - "CS0844"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0844"
ms.assetid: ccf74e01-292a-42d0-897c-8add7aee2118
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0844
宣言する前にローカル変数 'name' を使用することはできません。 ローカル変数の宣言によって、フィールド 'name' が非表示になります。  
  
 識別子は、所定のブロックで 1 つの意味のみを持つことができます。 クラス フィールドと同じ名前を持つローカル変数は、識別子の 2 番目の意味を導入することによって、フィールドを非表示にできます。 したがって、コンパイラは、メソッドでクラス フィールドを参照し、同じ名前でローカル変数を宣言すると、エラーを生成します。  
  
### このエラーを解決するには  
  
-   `this.num` を使用して、クラス フィールドを参照します。  
  
-   ローカル変数にクラス フィールドとは別の名前を付けます。  
  
## 使用例  
 次のコードでは CS0844 が生成されます。  
  
```  
class Test { int num; public void TestMethod() { num = 5; // CS0844 int num = 6;        } public static int Main() { return 1; } }  
```