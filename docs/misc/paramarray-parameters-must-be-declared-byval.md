---
title: "ParamArray パラメーターは、&#39;ByVal&#39; として宣言しなければなりません。 | Microsoft Docs"
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
  - "vbc30667"
  - "bc30667"
helpviewer_keywords: 
  - "BC30667"
ms.assetid: 583e231f-a4c9-47aa-ae37-7bac43b0b318
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ParamArray パラメーターは、&#39;ByVal&#39; として宣言しなければなりません。
`ParamArray` パラメーターは `ByRef` 修飾子を使用できません。  
  
 **エラー ID:** BC30667  
  
### このエラーを解決するには  
  
-   `ByVal` 修飾子を使用して `ParamArray` パラメーターを宣言します。  
  
## 参照  
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [ByVal](/dotnet/visual-basic/language-reference/modifiers/byval)