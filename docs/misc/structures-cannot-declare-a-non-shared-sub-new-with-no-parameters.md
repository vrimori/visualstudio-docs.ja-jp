---
title: "構造体で、共有されていない、パラメーターなしの &#39;Sub New&#39; を宣言することはできません | Microsoft Docs"
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
  - "vbc30629"
  - "bc30629"
helpviewer_keywords: 
  - "BC30629"
ms.assetid: f4298ef7-85b1-4543-b764-4c3abda84baa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 構造体で、共有されていない、パラメーターなしの &#39;Sub New&#39; を宣言することはできません
構造体の中で宣言された `Sub New` コンストラクターは、引数を受け入れるか、または `Shared` 修飾子で宣言する必要があります。  
  
 **エラー ID:** BC30629  
  
### このエラーを解決するには  
  
-   引数を受け入れるように `Sub New` コンストラクターを変更します。  
  
-   `Shared` 修飾子を適用して、コンストラクターを共有します。  
  
## 参照  
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Structures](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)