---
title: "&#39;Optional&#39; は、拡張メソッドの最初のパラメーターには適用できません | Microsoft Docs"
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
  - "bc36553"
  - "vbc36553"
helpviewer_keywords: 
  - "BC36553"
ms.assetid: 8ea0b90c-f155-47a9-988b-5b8009b510af
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Optional&#39; は、拡張メソッドの最初のパラメーターには適用できません
'Optional' は、拡張メソッドの最初のパラメーターには適用できません。 最初のパラメーターは、拡張する型を指定します。  
  
 拡張メソッドの最初のパラメーターでは、そのメソッドが拡張するデータ型を指定します。 メソッドが実行されると、最初のパラメーターは、そのメソッドを呼び出すデータ型のインスタンスにバインディングされます。 そのため、最初のパラメーターは必須であり、省略可能にできません。  
  
 この制限が適用されるのは、最初のパラメーターに対してのみです。 その他のパラメーターは省略可能な場合もそうでない場合もあり、他のメソッドと同じ規則に従います。 詳細については、「[Parameter List](/dotnet/visual-basic/language-reference/statements/parameter-list)」を参照してください。  
  
 **エラー ID:** BC36553  
  
### このエラーを解決するには  
  
-   拡張するデータ型を現在の最初のパラメーターで指定する場合、`Optional` キーワードを削除します。  
  
-   現在の最初のパラメーターがメソッドに対する標準パラメーターであり、拡張するデータ型をこのパラメーターで示さない場合は、新しい最初のパラメーターを追加してください。  
  
## 使用例  
 次の例の最初のパラメーターは、`Print` メソッドが `String` データ型を拡張することを示すに過ぎません。 したがって、省略可能にはできません。  
  
```  
<Extension()> Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 拡張メソッドが次のように呼び出される場合、そのメソッドのパラメーター `str` は `greeting` \(`Print` を呼び出す `String` のインスタンス\) にバインドされます。 コンパイラは、拡張メソッド `Print` の引数として `greeting` を使用します。  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [方法: プロシージャに対して省略可能なパラメーターを定義する \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0b32b312-0da0-489b-96ad-7dcb1f1f8f88)   
 [Optional Parameters](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)