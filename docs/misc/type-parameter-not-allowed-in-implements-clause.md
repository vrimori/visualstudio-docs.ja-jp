---
title: "型パラメーターは &#39;Implements&#39; 句では許可されていません | Microsoft Docs"
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
  - "vbc32056"
  - "bc32056"
helpviewer_keywords: 
  - "BC32056"
ms.assetid: a62d773b-e878-4817-8638-da49849477d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーターは &#39;Implements&#39; 句では許可されていません
ジェネリック型の `Implements` 句は、実装するメンバーとして型パラメーターを指定しています。  
  
 `Implements` 句は、インターフェイスとメンバーを指定する必要があります。 これは、インターフェイスに型パラメーターを渡すことはできますが、メンバーに渡すことやメンバーの名前として使用することはできません。  
  
 次のステートメントでは、このエラーが生成される可能性があります。  
  
```  
Class c1(Of t) Implements i1(Of t) Public Sub doSomething() Implements t End Class  
```  
  
 **エラー ID:** BC32056  
  
### このエラーを解決するには  
  
-   `Implements` キーワードの後に、インターフェイス名とインターフェイスの正規メンバーを指定します。 必要に応じて、インターフェイスに型パラメーターを渡すことができます。  
  
    ```  
    Public Sub doSomething() Implements i1(Of t).doSomething  
    ```  
  
## 参照  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [ビルド内にありません: Implements キーワードおよび Implements ステートメント](http://msdn.microsoft.com/ja-jp/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)