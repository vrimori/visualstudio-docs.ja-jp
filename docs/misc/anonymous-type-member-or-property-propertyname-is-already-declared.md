---
title: "匿名型のメンバーまたはプロパティ &#39;&lt;propertyname&gt;&#39; は既に宣言されています | Microsoft Docs"
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
  - "bc36547"
  - "vbc36547"
helpviewer_keywords: 
  - "BC36547"
ms.assetid: 4c60d24a-62d7-404a-bc35-d1a1d9c9f851
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 匿名型のメンバーまたはプロパティ &#39;&lt;propertyname&gt;&#39; は既に宣言されています
プロパティ名は、匿名型の宣言で 1 回だけ確立できます。 たとえば、次の宣言は無効です。  
  
```vb#  
'' Not valid, because the Label property is assigned to twice.  
' Dim anonType1 = New With {.Label = "Debra Garcia", .Label = .Label & ", President"}  
'' Not valid, because the property name inferred for both properties is  
'' Name.  
' Dim anonType2 = New With {Key product.Name, Key car1.Name}  
```  
  
 **エラー ID:** BC36547  
  
### このエラーを解決するには  
  
-   プロパティの 1 つには別の名前を選択してください。  
  
    ```vb#  
    ' Valid.  
    Dim anonType3 = New With {.Name = "Debra Garcia", .Label = .Name & ", President"}  
    ```  
  
-   名前と値を推定している変数またはプロパティに新しい名前を指定します。  
  
    ```vb#  
    ' Valid.  
    Dim anonType4 = New With {Key .ProductName = product.Name, Key .CarName = car1.Name}  
  
    ```  
  
## 参照  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)