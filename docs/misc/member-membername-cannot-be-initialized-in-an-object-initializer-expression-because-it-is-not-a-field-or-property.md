---
title: "メンバー &#39;&lt;membername&gt;&#39; はフィールドまたはプロパティではないため、オブジェクト初期化子式で初期化できません | Microsoft Docs"
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
  - "bc30990"
  - "vbc30990"
helpviewer_keywords: 
  - "BC30990"
ms.assetid: 3be2c135-20f6-49b2-a324-d213cfdf9ee3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メンバー &#39;&lt;membername&gt;&#39; はフィールドまたはプロパティではないため、オブジェクト初期化子式で初期化できません
オブジェクト初期化子リストに、共有メンバー、定数、またはメソッドの呼び出しを含めることはできません。 初期化子リスト内のメンバーはフィールドまたはプロパティである必要があり、プロパティのメンバーは引数を要求できません。  
  
 **エラー ID:** BC30990  
  
### このエラーを解決するには  
  
-   すべての共有メンバー、定数、メソッド呼び出し、またはパラメーターを持つプロパティをオブジェクト初期化子リストから削除します。  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [ビルド内にありません: Visual Basic の共有メンバー](http://msdn.microsoft.com/ja-jp/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [ビルド内にありません: プロパティとプロパティ プロシージャ](http://msdn.microsoft.com/ja-jp/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [ビルド内にありません: 既定のプロパティ](http://msdn.microsoft.com/ja-jp/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [ビルド内にありません: オブジェクト メンバー](http://msdn.microsoft.com/ja-jp/dfc2cc12-0e66-44fb-a78e-14f931db2309)   
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)