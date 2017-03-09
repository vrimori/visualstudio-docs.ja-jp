---
title: "&#39;New&#39; は、&#39;New&#39; 制約がない型パラメーターで使用できません | Microsoft Docs"
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
  - "bc32046"
  - "vbc32046"
helpviewer_keywords: 
  - "BC32046"
ms.assetid: 7ec6b52d-6fd5-47a0-b4a2-163bfd3dae35
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; は、&#39;New&#39; 制約がない型パラメーターで使用できません
宣言ステートメントで [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator) 句を使用して、作成する型として型パラメーターを指定し、その型パラメーターを `New` 制約なしで宣言しています。  
  
 型パラメーターに*制約*を設定すると、ジェネリック型が作成されるときにその型パラメーターに渡されるすべての型引数に要件が課されます。`New` 制約は、作成元のコードがアクセスできるパラメーターなしのコンストラクターを型引数が公開する必要があることを指定します。 これにより、宣言ステートメントの `New` 句でその型のインスタンスを作成できます。  
  
 **エラー ID:** BC32046  
  
### このエラーを解決するには  
  
-   アクセス可能なパラメーターなしのコンストラクターを型引数で公開するように要求できる場合は、型パラメーターの宣言に `New` 制約を追加します。  
  
-   アクセス可能なパラメーターなしのコンストラクターを型引数で公開するように要求できない場合は、宣言ステートメントから `New` 句を削除します。 その型パラメーターに渡されるすべての型引数でインスタンスを作成できることは保証できません。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)