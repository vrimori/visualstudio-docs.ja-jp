---
title: "インスタンス メンバーおよび &#39;Me&#39; を構造体のラムダ式内で使用することはできません | Microsoft Docs"
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
  - "vbc36638"
  - "bc36638"
helpviewer_keywords: 
  - "BC36638"
ms.assetid: 5c24a7c7-50f6-4ffb-9ed2-07e2abc4eaf3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# インスタンス メンバーおよび &#39;Me&#39; を構造体のラムダ式内で使用することはできません
構造体の内部から、この構造体のインスタンス メンバーを参照するか `Me` を使用するラムダ式を定義しました。 次のコードで、これらの 2 つの正しくない参照の例を示します。  
  
```vb#  
Structure Structure1 Public InstanceMember As Integer Public Function ExampleFun() As Integer '' The error is caused by use of InstanceMember. 'Dim fun1 = Function() InstanceMember '' The error is caused by use of Me. 'Dim fun2 = Function() Me.InstanceMember 'Return fun1() End Function End Structure  
```  
  
 **エラー ID:** BC36638  
  
### このエラーを解決するには  
  
-   インスタンス メンバーをローカル変数に代入し、そのローカル変数をステートメントで使用します。  
  
    ```vb#  
    Public Function ExampleFunFix() As Integer Dim temp = InstanceMember Dim fun1 = Function() temp Return fun1() End Function  
    ```  
  
## 参照  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Me](http://msdn.microsoft.com/ja-jp/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)