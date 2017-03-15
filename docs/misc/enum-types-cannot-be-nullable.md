---
title: "列挙型を Null 許容にすることはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32129"
  - "bc32129"
helpviewer_keywords: 
  - "BC32129"
ms.assetid: 9e0fe5c9-72c7-4905-b177-d00cc3469ea9
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 列挙型を Null 許容にすることはできません
列挙型を宣言するために使用される基になる型は、Null 許容にすることができません。 たとえば、次のコードでは、このエラーが発生します。  
  
```vb#  
'' Not valid. ' Enum exampleEnum As Integer? '     Member declarations. ' End Enum  
```  
  
 **エラー ID:** BC32129  
  
### このエラーを解決するには  
  
-   `Enum` 宣言で Null 許容の基になる型を使用しません。  
  
## 参照  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Enum Statement](/dotnet/visual-basic/language-reference/statements/enum-statement)