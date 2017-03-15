---
title: "メソッド &#39;&lt;procedurename&gt;&#39; に対して推定された型引数には、次の警告が表示されます: &lt;warninglist&gt; | Microsoft Docs"
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
  - "bc41006"
  - "vbc41006"
helpviewer_keywords: 
  - "BC41006"
ms.assetid: c789ffa9-0273-47f6-8915-78fc6a7d3d6d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッド &#39;&lt;procedurename&gt;&#39; に対して推定された型引数には、次の警告が表示されます: &lt;warninglist&gt;
ジェネリック プロシージャが型引数を指定せずに呼び出され、推定された型引数によって 1 つ以上の警告が生成されました。  
  
 通常、ジェネリック型を呼び出す場合は、ジェネリック型が定義する型パラメーターごとに型引数を指定します。 型引数を指定しない場合、コンパイラは型パラメーターに渡される型を推定しようとします。 推定された型があいまいな場合、または予期しない結果につながる可能性のある状況をもたらす場合、コンパイラによってこの警告が生成されます。  
  
 型パラメーターの*制約*は、型パラメーターに渡すことができる型引数を制限します。 たとえば、型パラメーターを <xref:System.IComparable%601> インターフェイスを実装するクラスに制限することができます。 詳細については、「[Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)」の「制約」を参照してください。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC41006  
  
### このエラーを解決するには  
  
-   ジェネリック プロシージャに型引数を指定し、コンパイラが型引数を推定しなくて済むようにします。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)