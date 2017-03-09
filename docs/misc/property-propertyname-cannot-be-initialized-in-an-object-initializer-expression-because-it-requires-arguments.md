---
title: "プロパティ &#39;&lt;propertyname&gt;&#39; には引数が必要なため、オブジェクト初期化子式で初期化できません | Microsoft Docs"
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
  - "bc30992"
  - "vbc30992"
helpviewer_keywords: 
  - "BC30992"
ms.assetid: a4d050b2-7366-457a-a852-8eb490c97573
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# プロパティ &#39;&lt;propertyname&gt;&#39; には引数が必要なため、オブジェクト初期化子式で初期化できません
オブジェクト初期化子リストで初期化されるメンバーはフィールドまたはプロパティである必要があり、プロパティのメンバーはパラメーターを持つことはできません。 たとえば、既定のプロパティには引数が必要なため、オブジェクト初期化子リストでこれらを初期化することはできません。 詳細については、「[ビルド内にありません: 既定のプロパティ](http://msdn.microsoft.com/ja-jp/a70f2a27-8176-4858-935e-f25afdd43ab5)」を参照してください。  
  
 **エラー ID:** BC30992  
  
### このエラーを解決するには  
  
-   引数を持つすべてのプロパティを初期化リストから削除します。  
  
## 使用例  
 次のクラスには、整数引数を必要とする既定のプロパティ `defaultProp` が含まれています。  
  
```  
Public Class SomeStrings Private myStrings() As String Sub New(ByVal size As Integer) ReDim myStrings(size) End Sub Default Property defaultProp(ByVal index As Integer) As String Get Return myStrings(index) End Get Set(ByVal Value As String) myStrings(index) = Value End Set End Property End Class  
```  
  
 既定のプロパティには引数が必要なため、次の宣言によりエラーが発生します。  
  
```  
' Dim strs As New SomeStrings(2) With { .defaultProp = "One" }  
```  
  
## 参照  
 [ビルド内にありません: 既定のプロパティ](http://msdn.microsoft.com/ja-jp/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [ビルド内にありません: プロパティとプロパティ プロシージャ](http://msdn.microsoft.com/ja-jp/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)