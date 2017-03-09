---
title: "匿名型は、少なくとも 1 つのメンバーを含んでいる必要があります | Microsoft Docs"
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
  - "bc36574"
  - "vbc36574"
helpviewer_keywords: 
  - "BC36574"
ms.assetid: fdc8dd47-ea38-49e8-8dd5-676f726cd101
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 匿名型は、少なくとも 1 つのメンバーを含んでいる必要があります
匿名型の宣言で初期化子リストを空にすることはできません。  
  
```  
' Not valid. ' Dim anonInstance = New With {}  
```  
  
 **エラー ID:** BC36574  
  
### このエラーを解決するには  
  
-   次のコードに示すように、中かっこ内のメンバーを宣言します。  
  
    ```  
    Dim anonInstance = New With {.MemberName = "value"}  
    ```  
  
## 参照  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)