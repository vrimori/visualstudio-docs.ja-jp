---
title: "メソッド &#39;&lt;methodname&gt;&#39; 内の型パラメーターのデータ型を、これらの引数から推論することはできません。 | Microsoft Docs"
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
  - "vbc36648"
  - "bc36645"
  - "bc36648"
  - "vbc36645"
helpviewer_keywords: 
  - "BC36648"
  - "BC36645"
ms.assetid: cc8c67bb-6cbb-4d7c-ba26-fe1d38908434
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッド &#39;&lt;methodname&gt;&#39; 内の型パラメーターのデータ型を、これらの引数から推論することはできません。
メソッド '\<methodname\>' 内の型パラメーターのデータ型を、これらの引数から推論することはできません。 データ型を明示的に指定すると、このエラーを修正できる場合があります。  
  
 型の推定を使用して、ジェネリック プロシージャの呼び出しの評価時に、型パラメーター \(またはパラメーター\) のデータ型 \(または型\) を決定しようとしました。 ただし、コンパイラはこのメソッドの型パラメーターのデータ型を検索することができず、エラーを報告します。  
  
> [!NOTE]
>  引数を指定できない \(たとえば、クエリ式のクエリ演算子\) 場合は、このエラー メッセージが 2 番目の文なしで表示されます。  
  
 たとえば、次のコードにこのエラーを示します。  
  
```vb#  
Module Module1 Sub Main() '' Not valid. 'GenericMethod("Hello", "World") End Sub Sub GenericMethod(Of T)(ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface  
```  
  
 **エラー ID:** BC36648 と BC36645  
  
### このエラーを解決するには  
  
-   型の推定に依存せずに、型パラメーターまたはパラメーターのデータ型を指定することができます。  
  
## 参照  
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)