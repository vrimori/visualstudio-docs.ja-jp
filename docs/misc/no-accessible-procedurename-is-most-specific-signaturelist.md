---
title: "最も固有な、アクセス可能な &#39;&lt;procedurename&gt;&#39; がありません: &lt;signaturelist&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30794"
  - "BC30794"
helpviewer_keywords: 
  - "BC30794"
ms.assetid: 51d54cbb-b530-4661-9952-5ccc17e4220b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 最も固有な、アクセス可能な &#39;&lt;procedurename&gt;&#39; がありません: &lt;signaturelist&gt;
代入ステートメントによって、オーバーロードされたプロシージャのアドレスがデリゲート変数に代入されましたが、コンパイラではオーバーロードされたバージョン間の解決ができません。  
  
 複数のオーバーロードされたバージョンで定義されたプロシージャのアドレスがコードで使用されている場合、コンパイラは使用するオーバーロードを判断する必要があります。 コンパイラは、デリゲート パラメーター リストとパラメーター リストが一致する単一のバージョンの検索を試行します。 詳細については、「[Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)」を参照してください。  
  
 コンパイラはシグネチャが一致するプロシージャを 2 つ以上検出すると、このエラーを生成します。 たとえば、あるジェネリック オーバーロードに型引数を渡すときに、別のオーバーロードと同じシグネチャがこのオーバーロードに与えられている場合に、これが発生する可能性があります。  
  
 **エラー ID:** BC30794  
  
### このエラーを解決するには  
  
-   この衝突が、他のオーバーロードと同じシグネチャを持つジェネリック オーバーロードによって発生している場合は、そのジェネリック オーバーロードに渡される型引数を変更します。  
  
## 参照  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [NOT IN BUILD: デリゲートと AddressOf 演算子](http://msdn.microsoft.com/ja-jp/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)