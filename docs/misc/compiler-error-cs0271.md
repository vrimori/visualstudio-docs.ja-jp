---
title: "コンパイラ エラー CS0271 | Microsoft Docs"
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
  - "CS0271"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0271"
ms.assetid: eadc9fb5-7770-4ec4-94f6-3c7cf37eec06
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0271
get アクセサーにアクセスできないため、プロパティまたはインデクサー 'property\/indexer' はこのコンテキストでは使用できません。  
  
 このエラーは、アクセス不能な `get` アクセサーにアクセスしようとした場合に発生します。 このエラーを解決するには、アクセサーのアクセシビリティを増やすか、呼び出し元の場所を変更します。 詳細については、「[アクセサーのアクセシビリティ](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility)」および「[プロパティ](/dotnet/csharp/programming-guide/classes-and-structs/properties)」を参照してください。  
  
 次の例では、CS0271 が生成されます。  
  
```  
// CS0271.cs public class MyClass { public int Property { private get { return 0; } set { } } public int Property2 { get { return 0; } set { } } } public class Test { public static void Main(string[] args) { MyClass c = new MyClass(); int a = c.Property;   // CS0271 int b = c.Property2;   // OK } }  
```