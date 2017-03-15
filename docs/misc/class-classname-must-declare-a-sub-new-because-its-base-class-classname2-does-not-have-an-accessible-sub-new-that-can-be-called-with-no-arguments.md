---
title: "基底クラス &#39;&lt;classname2&gt;&#39; に引数なしで呼び出せるアクセス可能な &#39;Sub New&#39; が指定されていないため、クラス &#39;&lt;classname&gt;&#39; は &#39;Sub New&#39; を宣言しなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30387"
  - "bc30387"
helpviewer_keywords: 
  - "BC30387"
ms.assetid: ff587e79-fa47-4b55-9a08-24688b209e0a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 基底クラス &#39;&lt;classname2&gt;&#39; に引数なしで呼び出せるアクセス可能な &#39;Sub New&#39; が指定されていないため、クラス &#39;&lt;classname&gt;&#39; は &#39;Sub New&#39; を宣言しなければなりません
派生クラスでコンストラクターが宣言されておらず、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] が呼び出す基底クラスのコンストラクターがないため、コンストラクターを生成できません。  
  
 派生クラスでコンストラクターが宣言されていない場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] は、`MyBase.New()` を呼び出す暗黙的なパラメーターなしのコンストラクターを生成しようとします。 引数を指定せずに呼び出すことができる基底クラスにアクセス可能なコンストラクターがない場合、または複数ある場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では暗黙的なコンストラクターを生成できません。  
  
 **エラー ID:** BC30387  
  
### このエラーを解決するには  
  
1.  派生クラスの任意の場所で少なくとも 1 つの `Sub New` コンストラクターを宣言し、実装します。  
  
2.  基底クラスのコンストラクター `MyBase.New()` への呼び出しを、すべての `Sub New` の最初の行として追加します。  
  
## 参照  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [ビルド内にありません: コンストラクターとデストラクターの使用](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Optional Parameters](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)   
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)