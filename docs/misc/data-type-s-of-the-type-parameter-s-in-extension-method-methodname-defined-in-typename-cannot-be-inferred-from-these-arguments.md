---
title: "&#39;&lt;typename&gt;&#39; で定義された拡張メソッド &#39;&lt;methodname&gt;&#39; 内の型パラメーターのデータ型を、これらの引数から推論することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36649"
  - "vbc36646"
  - "bc36646"
  - "vbc36649"
helpviewer_keywords: 
  - "BC36649"
  - "BC36646"
ms.assetid: 55274b01-6d78-4950-861e-07d9273ef76e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; で定義された拡張メソッド &#39;&lt;methodname&gt;&#39; 内の型パラメーターのデータ型を、これらの引数から推論することはできません
'\<typename\>' で定義された拡張メソッド '\<methodname\>' 内の型パラメーターのデータ型を、これらの引数から推論することはできません。 データ型を明示的に指定すると、このエラーが修正される可能性があります。  
  
 ジェネリック拡張メソッドの呼び出しを評価するときに、型の推定を使用して、1 つ以上の型パラメーターに対して 1 つ以上のデータ型を決定しようとしました。 ただし、コンパイラはこのメソッドの型パラメーターのデータ型を検索することができず、エラーを報告します。  
  
> [!NOTE]
>  引数の指定がオプションではない場合 \(たとえば、クエリ式内のクエリ演算子など\)、エラー メッセージの 2 つ目の文は表示されません。  
  
 次のコードにこのエラーを示します。  
  
```vb#  
Module Module1 Sub Main() Dim classInstance As ClassExample '' Not valid. 'classInstance.GenericExtensionMethod("Hello", "World") End Sub <System.Runtime.CompilerServices.Extension()> _ Sub GenericExtensionMethod(Of T)(ByVal classEx As ClassExample, _ ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface Class ClassExample End Class  
```  
  
 **エラー ID:** BC36649 and BC36646  
  
### このエラーを解決するには  
  
-   型の推定に依存せずに、型パラメーターまたはパラメーターのデータ型を指定できる場合があります。  
  
## 参照  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)