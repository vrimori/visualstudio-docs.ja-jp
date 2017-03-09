---
title: "明示的な初期化は、明示的な境界で宣言された配列に対しては許可されていません | Microsoft Docs"
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
  - "bc30672"
  - "vbc30672"
helpviewer_keywords: 
  - "BC30672"
ms.assetid: 4b525e8d-bde5-4408-8c10-7605ca039f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 明示的な初期化は、明示的な境界で宣言された配列に対しては許可されていません
配列は、特定のサイズになるように宣言している場合には初期化できません。  
  
 **エラー ID:** BC30672  
  
### このエラーを解決するには  
  
-   配列を宣言し、個別に初期化します。  
  
-   たとえば、動的配列として宣言および初期化し、必要に応じて `ReDim` を使用します。  
  
    ```  
    Dim A() As Integer = {0, 1, 2, 3} ReDim Preserve A(3)  
    ```  
  
## 参照  
 [配列](/dotnet/visual-basic/programming-guide/language-features/arrays/index)