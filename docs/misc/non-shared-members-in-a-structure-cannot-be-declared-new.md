---
title: "構造体内の共有されていないメンバーは &#39;New&#39; として宣言できません | Microsoft Docs"
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
  - "vbc30795"
  - "BC30795"
helpviewer_keywords: 
  - "BC30795"
ms.assetid: 8e4e1ad8-3bac-475f-82e8-e4f134692204
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 構造体内の共有されていないメンバーは &#39;New&#39; として宣言できません
構造体内の共有されていない変数が、`New` 句で宣言されています。  
  
 次のコード行が示すとおり、構造体内の共有される参照変数は初期化でき、共有しない参照変数は初期化せずに使用できます。  
  
 `Shared structVar1 As New System.ApplicationException`  
  
 `Dim structVar2 As System.ApplicationException`  
  
 しかし、構造体内の共有しない参照変数は初期化できません。 次のコード行は正しくありません。  
  
 `Dim structVar3 As New System.ApplicationException ' INVALID IN A STRUCTURE`  
  
 **エラー ID:** BC30795  
  
### このエラーを解決するには  
  
-   参照変数宣言から `Shared` 修飾子または `New` キーワードを削除します。  
  
## 参照  
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)