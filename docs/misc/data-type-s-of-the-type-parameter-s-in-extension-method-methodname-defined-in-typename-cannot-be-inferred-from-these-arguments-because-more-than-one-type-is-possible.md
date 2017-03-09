---
title: "&#39;&lt;typename&gt;&#39; で定義されている拡張メソッド &#39;&lt;methodname&gt;&#39; 内の型パラメーターのデータ型をこれらの引数から推論しようとしても、複数の型の可能性があるため、できません | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36655"
  - "vbc36652"
  - "vbc36655"
  - "bc36652"
helpviewer_keywords: 
  - "BC36655"
  - "BC36652"
ms.assetid: 49836f20-c877-4267-8bdc-6f6d108fb8c0
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; で定義されている拡張メソッド &#39;&lt;methodname&gt;&#39; 内の型パラメーターのデータ型をこれらの引数から推論しようとしても、複数の型の可能性があるため、できません
'\<typename\>' で定義されている拡張メソッド '\<methodname\>' 内の型パラメーターのデータ型をこれらの引数から推論しようとしても、複数の型の可能性があるため、できません。 データ型を明示的に指定すると、このエラーを修正できる場合があります。  
  
 ジェネリック拡張メソッドを呼び出すときに、型の推定を使用して型パラメーターの型を決定しようとしました。 コンパイラによって 1 つ以上の型パラメーターについて複数のデータ型の候補が検出されると、このエラーが報告されます。  
  
> [!NOTE]
>  引数を指定できない \(たとえば、クエリ式のクエリ演算子\) 場合は、このエラー メッセージが 2 番目の文なしで表示されます。  
  
 次のコードにこのエラーを示します。  
  
```vb#  
Option Strict Off Imports System.Runtime.CompilerServices Module Module1 Sub Main() Dim caller As New Class1 '' Not valid. 'caller.targetExtension(1, "2") End Sub <Extension()> _ Sub targetExtension(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **エラー ID:** BC36655 \([!INCLUDE[vbteclinq](../misc/includes/vbteclinq_md.md)] クエリ内\) と BC36652 \(クエリ外\)  
  
### このエラーを解決するには  
  
-   エラーがクエリの外部で出現する場合は、型パラメーターのデータ型を明示的に指定してみてください。  
  
    ```  
    caller.targetExtension(Of Integer)(1, "2") caller.targetExtension(Of String)(1, "2")  
    ```  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)