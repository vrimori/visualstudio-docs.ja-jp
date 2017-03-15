---
title: "コンパイラ エラー CS0119 | Microsoft Docs"
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
  - "CS0119"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0119"
ms.assetid: 048924f1-378f-4021-bd20-299d3218f810
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0119
'construct1\_name' は 'construct1' ですが、指定されたコンテキストでは有効ではありません  
  
 コンパイラで、次のような予期しない構成体が検出されました。  
  
-   クラス コンストラクターは、条件付きステートメントにおいて有効なテスト式ではありません。  
  
-   配列要素の参照に、インスタンス名ではなくクラス名が使用されました。  
  
-   メソッド識別子は、構造体またはクラスのように使用されます。  
  
## 使用例  
 次の例では CS0119 が生成されます。  
  
```  
// CS0119.cs using System; public class MyClass { public static void Test() {} public static void Main() { Console.WriteLine(Test.x);   // CS0119 } }  
```