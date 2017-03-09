---
title: "アクセス可能なすべてのオーバーロードには引数が必要なため、プロパティ &#39;&lt;propertyname&gt;&#39; はオブジェクト初期化子式で初期化できません | Microsoft Docs"
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
  - "bc30993"
  - "vbc30993"
helpviewer_keywords: 
  - "BC30993"
ms.assetid: d4476065-2ca2-4c9e-a571-c08917a6387f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# アクセス可能なすべてのオーバーロードには引数が必要なため、プロパティ &#39;&lt;propertyname&gt;&#39; はオブジェクト初期化子式で初期化できません
オブジェクト初期化子リストで初期化されるメンバーは、フィールドまたはプロパティのいずれかである必要があります。 また、初期化子リスト内のプロパティは、パラメーターを持つことはできません。 このエラーの原因であるプロパティはオーバーロードされ、その各バージョンには引数が必要です。 そのため、オブジェクト初期化子リストで、このプロパティを初期化することはできません。  
  
 **エラー ID:** BC30993  
  
### このエラーを解決するには  
  
-   初期化子リストから引数を必要とするプロパティを削除します。  
  
## 使用例  
 次のクラスには、3 つのプロパティ定義 \(`TotalItems` について 1 つ、`Item` について 2 つ\) が含まれ、このクラスはオーバーロードされます。  
  
```  
Class CollectionOfItems Property TotalItems() As Integer Get End Get Set(ByVal value As Integer) End Set End Property Property Item(ByVal Key As String) As Object Get End Get Set(ByVal value As Object) End Set End Property Property Item(ByVal Index As Integer) As Object Get End Get Set(ByVal value As Object) End Set End Property End Class  
```  
  
 `TotalItems` プロパティには引数が必要ないため、次の宣言に示すように、オブジェクト初期化リストで初期化できます。  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 }  
```  
  
 `Item` プロパティはオーバーロードされ、各オーバーロードには引数が必要です。 そのため、オブジェクト初期化子リストに `Item` を含めることはできません。  
  
```  
' The following declaration is not valid. ' Dim coinCollection As New CollectionOfItems With { .TotalItems = 0, _ '    .Item = aCoinObject }  
```  
  
 このエラーを回避するには、オブジェクト初期化子の外で `Item` プロパティを初期化します。  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 } coinCollection.Item(1) = aCoinObject  
```  
  
## 参照  
 [ビルド内にありません: プロパティとプロパティ プロシージャ](http://msdn.microsoft.com/ja-jp/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [How to: Call a Property Procedure](../Topic/How%20to:%20Call%20a%20Property%20Procedure%20\(Visual%20Basic\).md)   
 [ビルド内にありません: 既定のプロパティ](http://msdn.microsoft.com/ja-jp/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)