---
title: "ステートメントをインターフェイス本体内部に記述することはできません (Visual Basic エラー)。 | Microsoft Docs"
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
  - "bc30604"
  - "vbc30604"
helpviewer_keywords: 
  - "BC30604"
ms.assetid: ce4759fe-5e49-43ad-8405-a3f46ed0a36f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ステートメントをインターフェイス本体内部に記述することはできません (Visual Basic エラー)。
予期しない言語構成要素が見つかりました。`End Interface` 構成要素が不足しており、この時点より後のソース コードがインターフェイス外であると想定されます。  
  
 **エラー ID:** BC30604  
  
### このエラーを解決するには  
  
1.  インターフェイス定義内で使用されるコードの構文を確認します。  
  
2.  インターフェイス定義が `End Interface` 構成要素で終了していることを確認します。  
  
## 参照  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)