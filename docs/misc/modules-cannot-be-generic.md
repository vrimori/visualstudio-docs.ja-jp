---
title: "モジュールを汎用にはできません | Microsoft Docs"
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
  - "BC32073"
  - "vbc32073"
helpviewer_keywords: 
  - "BC32073"
ms.assetid: 47246e2b-51d4-4a10-a3ac-bc77b44fa2ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# モジュールを汎用にはできません
`Module` ステートメントは `Of` キーワードを使用して、ジェネリック型パラメーターを組み込んでいます。  
  
 ジェネリック クラス、構造体、インターフェイス、プロシージャ、およびデリゲートを定義して使用することができます。 ジェネリック モジュールは定義できません。  
  
 **エラー ID:** BC32073  
  
### このエラーを解決するには  
  
1.  `Module` ステートメントから `Of` キーワードを削除します。  
  
2.  ジェネリック モジュールの機能が必要な場合、最も近いものはジェネリック クラスです。`Module` ステートメントではなく [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement) を使用します。  
  
## 参照  
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [方法 : 複数のデータ型に同一の機能を提供できるクラスを定義する](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)