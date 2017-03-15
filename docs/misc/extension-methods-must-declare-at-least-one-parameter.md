---
title: "拡張メソッドは、少なくとも 1 つのパラメーターを宣言する必要があります | Microsoft Docs"
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
  - "vbc36552"
  - "bc36552"
helpviewer_keywords: 
  - "BC36552"
ms.assetid: a8cc8cdd-cdb5-42ca-b5a1-c9a71abd46eb
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 拡張メソッドは、少なくとも 1 つのパラメーターを宣言する必要があります
拡張メソッドは、少なくとも 1 つのパラメーターを宣言する必要があります。 最初のパラメーターは、拡張する型を指定します。  
  
 最初のパラメーターはそのメソッドが拡張するデータ型を指定するため、パラメーターを持たない拡張メソッドは無効です。 最初のパラメーターは、そのメソッドを呼び出すデータ型のインスタンスにバインドされます。  
  
 **エラー ID:** BC36552  
  
### このエラーを解決するには  
  
-   メソッドが拡張する型のパラメーターを追加します。  
  
## 使用例  
 次の例の最初のパラメーターは、`Print` メソッドが `String` データ型を拡張することを示しています。  
  
```  
<Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 拡張メソッドが次のように呼び出される場合、そのメソッドのパラメーター `str` は `greeting` \(`Print` を呼び出す `String` のインスタンス\) にバインドされます。 コンパイラは、拡張メソッド `Print` の引数として `greeting` を使用します。  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Procedure Parameters and Arguments](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)   
 [Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/index)