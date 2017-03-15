---
title: "構造体 &#39;&lt;structurename&gt;&#39; には、少なくとも 1 つのインスタンス メンバー変数またはイベント宣言を含める必要があります | Microsoft Docs"
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
  - "bc30281"
  - "vbc30281"
helpviewer_keywords: 
  - "BC30281"
ms.assetid: a03ee4e2-5fea-4933-898f-7f125b25824e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 構造体 &#39;&lt;structurename&gt;&#39; には、少なくとも 1 つのインスタンス メンバー変数またはイベント宣言を含める必要があります
機能的に空の構造体が生成されます。 少なくとも 1 つの変数メンバーを `Structure` ステートメントと `End Structure` ステートメントの間で宣言する必要があります。  
  
 **エラー ID:** BC30281  
  
### このエラーを解決するには  
  
-   `Dim` ステートメントまたは `Event` ステートメントを構造体に追加します。  
  
## 参照  
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)