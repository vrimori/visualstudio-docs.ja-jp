---
title: "コンパイラ エラー CS0546 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0546"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0546"
ms.assetid: d259c86f-ee29-4e2d-b381-6ba7252af87e
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0546
'accessor': 'property' に、オーバーライド可能な set アクセサーがないため、オーバーライドできません。  
  
 アクセサーをオーバーライドできないために、プロパティのアクセサー メソッドのオーバーライドに失敗しました。 このエラーは、次の場合に発生する可能性があります。  
  
-   基底クラス プロパティが [virtual](/dotnet/csharp/language-reference/keywords/virtual) として宣言されていません。  
  
-   基底クラスのプロパティが、オーバーライドする [get](/dotnet/csharp/language-reference/keywords/get) または [set](/dotnet/csharp/language-reference/keywords/set) アクセサーを宣言していません。  
  
 基底クラス プロパティをオーバーライドしない場合、派生クラスでプロパティの前に [new](/dotnet/csharp/language-reference/keywords/new) キーワードを使用することができます。  
  
 詳細については、「[プロパティの使用](/dotnet/csharp/programming-guide/classes-and-structs/using-properties)」を参照してください。  
  
## 使用例  
 次の例では、基底クラスでプロパティの set アクセサーが宣言されていないため、CS0546 エラーが生成されます。  
  
```  
// CS0546.cs // compile with: /target:library public class a { public virtual int i { get { return 0; } } public virtual int i2 { get { return 0; } set {} } } public class b : a { public override int i { set {}   // CS0546 error no set } public override int i2 { set {}   // OK } }  
```  
  
## 参照  
 [プロパティ](/dotnet/csharp/programming-guide/classes-and-structs/properties)