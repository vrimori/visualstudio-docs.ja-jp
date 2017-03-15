---
title: "コンパイラ エラー CS0265 | Microsoft Docs"
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
  - "CS0265"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0265"
ms.assetid: d43d19c2-8a66-4bb1-95a0-557b0a29bce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0265
'type' の partial 宣言には、型パラメーター 'type parameter' に対して矛盾する制約が含まれています  
  
 このエラーは、ジェネリック クラスを部分クラスとして定義したとき、つまり部分定義が複数の場所に出現するときに、ジェネリック型に対する制約が複数の場所で矛盾しているか、異なっている場合に発生します。 複数の場所で制約を指定する場合は、すべて同じにする必要があります。 最も簡単な解決策は、制約を 1 つの場所で指定し、それ以外の場所では制約を省略することです。 詳細については、次のトピックを参照してください。[部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods) および[型パラメーターの制約](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
 次のコードではエラー CS0265 が生成されます。  
  
## 使用例  
 このコードでは、部分クラス定義がすべて 1 つのファイル内に記述されていますが、複数のファイルに分けることもできます。  
  
```  
// CS0265.cs public class GenericsErrors { interface IFace1 { } interface IFace2 { } partial class PartialBadBounds<T> where T : IFace1 { } // CS0265 partial class PartialBadBounds<T> where T : IFace2 { } }  
```