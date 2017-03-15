---
title: "&#39;&lt;derivedclassname&gt;&#39; の基底クラス &#39;&lt;baseclassname&gt;&#39; にある &#39;&lt;constructorname&gt;&#39; が古い形式としてマークされているため、この &#39;Sub New&#39; の最初のステートメントは、&#39;MyBase.New&#39; または &#39;MyClass.New&#39; の明示的な呼び出しである必要があります: &#39;&lt;errormessage&gt;&#39; | Microsoft Docs"
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
  - "bc41004"
  - "vbc41004"
helpviewer_keywords: 
  - "BC41004"
ms.assetid: 61185283-d43d-46ae-bfa0-6fe3e1d0982a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;derivedclassname&gt;&#39; の基底クラス &#39;&lt;baseclassname&gt;&#39; にある &#39;&lt;constructorname&gt;&#39; が古い形式としてマークされているため、この &#39;Sub New&#39; の最初のステートメントは、&#39;MyBase.New&#39; または &#39;MyClass.New&#39; の明示的な呼び出しである必要があります: &#39;&lt;errormessage&gt;&#39;
クラス コンストラクターが基底クラスのコンストラクターを明示的に呼び出さず、暗黙的な基底クラスのコンストラクターが <xref:System.ObsoleteAttribute> 属性および警告として扱うことを示すディレクティブでマークされています。  
  
 派生クラスのコンストラクターが基底クラスのコンストラクターを呼び出さない場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、パラメーターなしの基底クラスのコンストラクターの暗黙的な呼び出しを生成しようとします。 引数を指定せずに呼び出すことができるアクセス可能なコンストラクターが基底クラスにない場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では暗黙的な呼び出しを生成できません。 この場合、必要なコンストラクターが <xref:System.ObsoleteAttribute> 属性でマークされるため、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では呼び出すことができません。  
  
 <xref:System.ObsoleteAttribute> を適用することで、使用されなくなった要素としてすべてのプログラミング要素にマークを付けることができます。 これを行う場合、この属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` のどちらかに設定できます。`True` に設定した場合、この要素を使用しようとすると、コンパイラはエラーとして処理します。`False` に設定するか、または既定の `False` にする場合、この要素を使用しようとすると、コンパイラは警告を発行します。  
  
 既定では、<xref:System.ObsoleteAttribute> の <xref:System.ObsoleteAttribute.IsError%2A> プロパティが `False` であるため、このメッセージは警告となります。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」をご覧ください。  
  
 **エラー ID:** BC41004  
  
### このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、適切な処理を行います。  
  
2.  `MyBase.New()` または `MyClass.New()` の呼び出しを `Sub New` の最初のステートメントとして派生クラスに含めます。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)