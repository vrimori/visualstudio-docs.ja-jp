---
title: "予期しない型引数です | Microsoft Docs"
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
  - "vbc32088"
  - "bc32088"
helpviewer_keywords: 
  - "BC32088"
ms.assetid: a0918e90-e7ad-4edc-81e1-584e6174bb6c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 予期しない型引数です
`Implements` 句では、実装するインターフェイス メンバーの型引数を指定します。  
  
 `Implements` 句では、実装するインターフェイスおよびメンバーのみを識別する必要があります。 つまり、ジェネリック プロシージャを宣言する場合は、インターフェイス プロシージャを実装しない場合と同様に、`Of` 句と型引数を宣言の本体に配置する必要があります。  
  
 次のコードでは、このエラーが生成される可能性があります。  
  
```  
Public Interface testInterface Sub testSub(Of t)() End Interface Public Class testClass Implements testInterface Public Sub testSub() Implements testInterface.testSub(Of t)() End Sub End Class  
```  
  
 `Implements` 句の前の宣言は、アクセスまたはプロシージャ修飾子が追加される可能性がある点を除き、インターフェイス定義のようになります。 次のコードでは、エラーが回避されます。  
  
```  
Public Sub testSub(Of t)() Implements testInterface.testSub  
```  
  
 **エラー ID:** BC32088  
  
### このエラーを解決するには  
  
-   `Implements` 句から型引数リストを削除します。  
  
-   インターフェイスのジェネリック メンバーを実装する場合は、型引数リストを宣言の本体の `Implements` キーワードの前に配置します。  
  
## 参照  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [ビルド内にありません: Implements キーワードおよび Implements ステートメント](http://msdn.microsoft.com/ja-jp/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)