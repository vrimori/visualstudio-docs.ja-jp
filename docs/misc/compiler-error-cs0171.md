---
title: "コンパイラ エラー CS0171 | Microsoft Docs"
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
  - "CS0171"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0171"
ms.assetid: 8c1d76c9-1048-4579-9031-23e3566e6288
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0171
自動的に実装されたプロパティ 'name' のバッキング フィールドは、コントロールが呼び出し元に返される前に完全に割り当てられている必要があります。 コンストラクター初期化子から既定のコンストラクターを呼び出すことをご検討ください。  
  
 [構造体](/dotnet/csharp/language-reference/keywords/struct)内のコンストラクターは、その構造体のすべてのフィールドを初期化する必要があります。 詳細については、「[コンストラクター](/dotnet/csharp/programming-guide/classes-and-structs/constructors)」を参照してください。  
  
 次の例では CS0171 が生成されます。  
  
```  
// CS0171.cs struct MyStruct { MyStruct(int initField)   // CS0171 { // i = initField;      // uncomment this line to resolve this error } public int i; } class MyClass { public static void Main() { MyStruct aStruct = new MyStruct(); } }  
```