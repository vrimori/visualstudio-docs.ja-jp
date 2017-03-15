---
title: "&#39;&lt;modulename&gt;&#39; で定義された拡張メソッド &#39;&lt;methodname&gt;&#39; はジェネリックではない (または自由型パラメーターがない) ため、型引数を指定できません | Microsoft Docs"
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
  - "bc36907"
  - "vbc36907"
helpviewer_keywords: 
  - "BC36907"
ms.assetid: 45191e93-89d1-48ec-99a5-ff9661a2a6ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;modulename&gt;&#39; で定義された拡張メソッド &#39;&lt;methodname&gt;&#39; はジェネリックではない (または自由型パラメーターがない) ため、型引数を指定できません
ジェネリック パラメーターがないか、型が既に指定されていないジェネリック パラメーターがない拡張メソッドの呼び出しで、型引数が指定されています。 たとえば、次のコードでは、このエラーが発生します。  
  
```vb#  
' The extension method is not generic. <Extension()> _ Sub Example(ByVal str As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
Dim str = "hi" '' The call to Example specifies a type argument. '' Not valid. 'str.Example(Of String)()  
```  
  
 **エラー ID:** BC36907  
  
### このエラーを解決するには  
  
-   拡張メソッド定義に型パラメーターを追加します。  
  
-   プロシージャ呼び出しから余分な型引数を削除します。  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)