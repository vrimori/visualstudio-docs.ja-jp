---
title: "&#39;&lt;typeName&gt;&#39; で定義された拡張メソッド &#39;&lt;methodName&gt;&#39; に、デリゲート &#39;&lt;delegateName&gt;&#39; と同じシグネチャがありません | Microsoft Docs"
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
  - "bc36580"
  - "vbc36580"
helpviewer_keywords: 
  - "BC36580"
ms.assetid: dc6b6a63-02b0-43d8-b6a7-c1cd397c6ee3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typeName&gt;&#39; で定義された拡張メソッド &#39;&lt;methodName&gt;&#39; に、デリゲート &#39;&lt;delegateName&gt;&#39; と同じシグネチャがありません
拡張メソッドのシグネチャと、使用しようとしているデリゲートのシグネチャが一致していません。`Delegate` ステートメントは、デリゲート クラスのパラメーターの型と戻り値の型を定義します。 パラメーター、型、および戻り値の型が一致するプロシージャを使用すると、このデリゲート型のインスタンスを作成できます。 次の例では、拡張メソッド `Example` のシグネチャと、デリゲート `Del` のシグネチャに互換性がないため、このエラーが発生します。  
  
```vb#  
' Definition of the delegate, with two parameters. Delegate Sub Del(ByVal m As Integer, ByVal s As String)  
```  
  
```vb#  
' Definition of the extension method, with one parameter. <Extension()> _ Sub Example(ByVal s As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
'' This assignment causes the error. ' Dim exampleDel As Del = AddressOf Example  
```  
  
 **エラー ID:** BC36580  
  
### このエラーを解決するには  
  
-   デリゲートと拡張メソッドに同じ数のパラメーターがあることを確認します。  
  
-   デリゲートと拡張メソッドで、パラメーターの順序が同じになっていることを確認します。  
  
-   各パラメーターのデータ型と、対応する拡張メソッドのパラメーターを比較して、互換性があることを確認します。  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)