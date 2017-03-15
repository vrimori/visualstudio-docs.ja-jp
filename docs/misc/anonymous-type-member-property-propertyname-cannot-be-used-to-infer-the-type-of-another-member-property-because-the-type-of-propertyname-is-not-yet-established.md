---
title: "&#39;&lt;propertyname&gt;&#39; の型がまだ確立されていないため、匿名型メンバーのプロパティ &#39;&lt;propertyname&gt;&#39; を使用して別のメンバーのプロパティの型を推論することはできません | Microsoft Docs"
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
  - "vbc36559"
  - "bc36559"
helpviewer_keywords: 
  - "BC36559"
ms.assetid: 58ab8d35-9d85-4aca-8b4e-f232d7e4af61
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;propertyname&gt;&#39; の型がまだ確立されていないため、匿名型メンバーのプロパティ &#39;&lt;propertyname&gt;&#39; を使用して別のメンバーのプロパティの型を推論することはできません
匿名型のプロパティの型を確立するまでは、そのプロパティを使用して別のプロパティの型を確立することはできません。 たとえば、以下の宣言では、`.LastName` がまだ初期化されていないので、`.IDName = .LastName` は正しくありません。  
  
```  
' Not valid.   
' Dim anon1 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}   
```  
  
 **エラー ID:** BC36559  
  
### このエラーを解決するには  
  
-   プロパティの型を確立してから、そのプロパティを使用して別のプロパティを初期化するようにします。  
  
    ```  
    Dim anon2 = New With {Key .LastName = "Jones", Key .IDName = .LastName}  
    ```  
  
## 参照  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)