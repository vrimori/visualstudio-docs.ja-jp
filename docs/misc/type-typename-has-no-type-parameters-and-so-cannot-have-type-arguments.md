---
title: "&#39;&lt;typename&gt;&#39; には型パラメーターが指定されてないため、型引数を指定できません | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32045"
  - "vbc32045"
helpviewer_keywords: 
  - "BC32045"
ms.assetid: b86e784c-6718-4585-bd39-2f0982068828
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; には型パラメーターが指定されてないため、型引数を指定できません
非ジェネリック型を呼び出す際に、宣言ステートメントまたは代入ステートメントに [Of](/dotnet/visual-basic/language-reference/statements/of-clause) 句が含まれています。  
  
 その定義によって、*ジェネリック型*は、クラス、構造体、インターフェイス、プロシージャ、またはデリゲートになり、1 つ以上の*型パラメーター*で指定できるデータ型で動作します。 コードを使用してこのジェネリック型から型を作成すると、型パラメーターそれぞれに*型引数*が指定されます。 型の作成の一環として、型引数はそれぞれ、生成されたコード内にある対応する型パラメーターの出現個所をすべて置換します。  
  
 型パラメーターはかっこ内の `Of` 句を使用して定義され、型引数はかっこ内の `Of` 句を使用して指定されます。`Of` 句は、ジェネリック型を処理する場合にのみ使用されます。  
  
 非ジェネリック型は型パラメーターを受け入れません。このような型を呼び出す場合は、型引数を指定できません。  
  
 **エラー ID:** BC32045  
  
### このエラーを解決するには  
  
1.  宣言ステートメントまたは代入ステートメントで使用している型のスペルを確認します。  
  
2.  非ジェネリック型を呼び出す場合は、`Of` 句と、それにかっこがあればかっこを削除します。 プロシージャ、デリゲート、またはクラス コンストラクターの通常の引数リストを囲むかっこは削除しないでください。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [方法 : ジェネリック クラスを使用する](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)