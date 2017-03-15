---
title: "&#39;&lt;derivedclassname&gt;&#39; の基底クラス &#39;&lt;baseclassname&gt;&#39; にある &#39;&lt;constructorname&gt;&#39; が古い形式に設定されているため、この &#39;Sub New&#39; の最初のステートメントは、明示的な &#39;MyBase.New&#39; または &#39;MyClass.New&#39; への呼び出しでなければなりません。 | Microsoft Docs"
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
  - "vbc30919"
  - "bc30919"
helpviewer_keywords: 
  - "BC30919"
ms.assetid: 437e3204-8ddc-45d3-b9b4-c66d53a61a6d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;derivedclassname&gt;&#39; の基底クラス &#39;&lt;baseclassname&gt;&#39; にある &#39;&lt;constructorname&gt;&#39; が古い形式に設定されているため、この &#39;Sub New&#39; の最初のステートメントは、明示的な &#39;MyBase.New&#39; または &#39;MyClass.New&#39; への呼び出しでなければなりません。
クラス コンストラクターが基底クラスのコンストラクターを明示的に呼び出さず、暗黙的な基底クラスのコンストラクターが <xref:System.ObsoleteAttribute> 属性およびエラーとして扱うことを示すディレクティブでマークされています。  
  
 派生クラスのコンストラクターが基底クラスのコンストラクターを呼び出さない場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、パラメーターなしの基底クラスのコンストラクターの暗黙的な呼び出しを生成しようとします。 引数を指定せずに呼び出すことができる基底クラスにアクセス可能なコンストラクターがない場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では暗黙的な呼び出しを生成できません。 この場合、必要なコンストラクターが <xref:System.ObsoleteAttribute> 属性でマークされるため、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では呼び出すことができません。  
  
 <xref:System.ObsoleteAttribute> を適用することで、使用されなくなった要素としてすべてのプログラミング要素にマークを付けることができます。 これを行う場合、この属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` のどちらかに設定できます。`True` に設定した場合、コンパイラは、この要素を使用する試行をエラーとして処理します。`False` に設定するか、または既定の `False` にする場合、この要素の使用が試行されると、コンパイラは警告を発行します。  
  
 **エラー ID:** BC30919  
  
### このエラーを解決するには  
  
-   `MyBase.New()` または `MyClass.New()` の呼び出しを `Sub New` の最初のステートメントとして派生クラスに含めます。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)