---
title: "変数 &#39;&lt;variablename&gt;&#39; の Null 許容型を推論できません | Microsoft Docs"
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
  - "bc36628"
  - "vbc36628"
helpviewer_keywords: 
  - "BC36628"
ms.assetid: 3e92ae19-6a19-4b0b-9dd9-fba31cdb85a6
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 変数 &#39;&lt;variablename&gt;&#39; の Null 許容型を推論できません
Null 許容型は、配列、クラス、`String` などの参照型から推論できません。 データ型の推論元となる値は、値型である必要があります。 このエラーが発生するコード例を次に示します。  
  
```vb#  
'' Not valid.   
'Dim arrList? = New ArrayList  
'Dim except? = New Exception  
'Dim obj? = New Object  
'Dim stringVar? = "Open the application."  
  
' Valid.  
Dim intVar? = 10  
```  
  
 **エラー ID:** BC36628  
  
### このエラーを解決するには  
  
-   Null 許容の指定を削除します。  
  
## 参照  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)