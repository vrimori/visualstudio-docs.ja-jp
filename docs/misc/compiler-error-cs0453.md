---
title: "コンパイラ エラー CS0453 | Microsoft Docs"
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
  - "CS0453"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0453"
ms.assetid: a1bbd09e-6313-4bfd-84bf-bc15a8d214a6
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0453
型 'Type Name' は、ジェネリック型のパラメーター 'Parameter Name'、またはメソッド 'Generic Identifier' として使用するために、Null 非許容の値型である必要があります  
  
 このエラーは、**value** 制約があるジェネリック型またはメソッドのインスタンス化で非値型引数を使用すると発生します。 Null 許容値型引数を使用する場合にも発生することがあります。 次に示すコード例の最後の 2 行を参照してください。  
  
## 使用例  
 次のコードではこのエラーが生成されます。  
  
```  
// CS0453.cs using System; public class HV<S> where S : struct { } public class H1 : HV<string> { }                   // CS0453 public class H2 : HV<H1> { }                       // CS0453 public class H3<S> : HV<S> where S : class { }     // CS0453 public class H4 : HV<int?> { }                     // CS0453 public class H5 : HV<Nullable<Nullable<int>>> { }  // CS0453  
```