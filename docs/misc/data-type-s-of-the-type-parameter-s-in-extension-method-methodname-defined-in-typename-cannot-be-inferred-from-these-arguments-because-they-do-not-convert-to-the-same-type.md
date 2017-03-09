---
title: "&#39;typename&#39; で定義されている拡張メソッド &#39;&lt;methodname&gt;&#39; 内の型パラメーターのデータ型をこれらの引数から推論しようとしても、同じ型に変換されないため、できません。 | Microsoft Docs"
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
  - "vbc36658"
  - "bc36661"
  - "vbc36661"
  - "bc36658"
helpviewer_keywords: 
  - "BC36661"
  - "BC36658"
ms.assetid: 0bff97fd-cbe9-4433-8192-6498c6fb5d04
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;typename&#39; で定義されている拡張メソッド &#39;&lt;methodname&gt;&#39; 内の型パラメーターのデータ型をこれらの引数から推論しようとしても、同じ型に変換されないため、できません。
'typename' で定義されている拡張メソッド '\<methodname\>' 内の型パラメーターのデータ型をこれらの引数から推論しようとしても、同じ型に変換されないため、できません。 データ型を明示的に指定すると、このエラーを修正できる場合があります。  
  
 ジェネリック拡張メソッドの呼び出しを評価するときに、型の推定を使用して、1 つ以上の型パラメーターに対して 1 つ以上のデータ型を決定しようとしました。 コンパイラは、すべての引数の制約を満たすデータ型を見つけることができませんでした。 そのため、このエラーが報告されました。  
  
> [!NOTE]
>  引数を指定できない \(たとえば、クエリ式のクエリ演算子\) 場合は、このエラー メッセージが 2 番目の文なしで表示されます。  
  
 次のコードにこのエラーを示します。  
  
```vb#  
Option Strict Off Module Module3 Sub Main() Dim c1 As New Class1 '' Not valid. Integer and Date do not convert to the same type. 'c1.targetMethod(19, #3/4/2007#) End Sub <System.Runtime.CompilerServices.Extension()> _ Sub targetMethod(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **エラー ID:** BC36661 および BC36658  
  
### このエラーを解決するには  
  
-   次のコードに示されているように、互換性のある型に 1 つ以上の引数を明示的に変換することができます。  
  
    ```  
    c1.targetMethod(19, #3/4/2007#.ToOADate)  
    ```  
  
-   次のコードに示されているように、引数が変換する型パラメーターにデータ型を指定することができます。  
  
    ```  
    c1.targetMethod(Of String)(19, #3/4/2007#)  
    ```  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)