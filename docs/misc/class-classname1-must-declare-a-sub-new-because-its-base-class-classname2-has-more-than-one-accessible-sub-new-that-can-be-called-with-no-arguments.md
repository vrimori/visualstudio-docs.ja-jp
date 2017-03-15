---
title: "基底クラス &#39;&lt;classname2&gt;&#39; に引数なしで呼び出されるアクセス可能な &#39;Sub New&#39; が 2 つ以上指定されているため、クラス &#39;&lt;classname1&gt;&#39; で &#39;Sub New&#39; を宣言する必要があります | Microsoft Docs"
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
  - "bc32036"
  - "vbc32036"
helpviewer_keywords: 
  - "BC32036"
ms.assetid: 9b96387e-337e-4b2a-b49f-783c7e13811a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 基底クラス &#39;&lt;classname2&gt;&#39; に引数なしで呼び出されるアクセス可能な &#39;Sub New&#39; が 2 つ以上指定されているため、クラス &#39;&lt;classname1&gt;&#39; で &#39;Sub New&#39; を宣言する必要があります
派生クラスでコンストラクターが宣言されておらず、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] は呼び出す基底クラスのコンストラクターを特定できないため、コンストラクターを生成できません。  
  
 派生クラスでコンストラクターが宣言されていない場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] は、`MyBase.New()` を呼び出す暗黙的なパラメーターなしのコンストラクターを生成しようとします。 引数を指定せずに呼び出すことができる基底クラスにアクセス可能なコンストラクターがない場合、または複数ある場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では暗黙的なコンストラクターを生成できません。  
  
 この状況は、たとえば、1 つの基底クラスのコンストラクターに 1 つの `Optional` 引数があり、別の基底クラスのコンストラクターに 1 つの `ParamArray` 引数がある場合に発生することがあります。 これらの基底クラスのコンストラクターはそれぞれ引数なしで呼び出すことができます。  
  
 **エラー ID:** BC32036  
  
### このエラーを解決するには  
  
1.  派生クラスの任意の場所で少なくとも 1 つの `Sub New` コンストラクターを宣言し、実装します。  
  
2.  基底クラスのコンストラクター `MyBase.New()` への呼び出しを、すべての `Sub New` の最初の行として追加します。  
  
## 参照  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [ビルド内にありません: コンストラクタとデストラクタの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Optional Parameters](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)   
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)