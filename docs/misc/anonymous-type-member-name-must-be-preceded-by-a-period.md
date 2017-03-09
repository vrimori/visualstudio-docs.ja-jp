---
title: "匿名型のメンバー名の前には、ピリオドが必要です | Microsoft Docs"
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
  - "vbc36575"
  - "bc36575"
helpviewer_keywords: 
  - "BC36575"
ms.assetid: b87be29e-39f0-4830-9969-608d71137e3e
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 匿名型のメンバー名の前には、ピリオドが必要です
匿名型の宣言のオブジェクト初期化子リストでは、値が割り当てられる新しいメンバー名の前にピリオドが必要です。 次の例で、正しい宣言と正しくない宣言を示します。  
  
```vb#  
' Valid.  
Dim instanceName1 = New With {.memberName = 10}  
' Invalid declaration that causes this error.  
' Dim instanceName2 = New With {memberName = 10}  
```  
  
 **エラー ID:** BC36575  
  
### このエラーを解決するには  
  
-   メンバー名の前にピリオドを追加します。  
  
## 参照  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)