---
title: "クラス &#39;&lt;classname&gt;&#39; は、基底クラス &#39;&lt;baseclassname&gt;&#39; にある &#39;&lt;constructorname&gt;&#39; が古い形式に設定されているため、&#39;Sub New&#39; を宣言する必要があります | Microsoft Docs"
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
  - "bc41001"
  - "vbc41001"
helpviewer_keywords: 
  - "BC41001"
ms.assetid: b2c6b996-6d52-4963-9fee-8b6f78fc028c
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# クラス &#39;&lt;classname&gt;&#39; は、基底クラス &#39;&lt;baseclassname&gt;&#39; にある &#39;&lt;constructorname&gt;&#39; が古い形式に設定されているため、&#39;Sub New&#39; を宣言する必要があります
クラス宣言にコンストラクターが含まれず、基底クラスのコンストラクターが <xref:System.ObsoleteAttribute> 属性および警告として扱うことを示すディレクティブでマークされています。  
  
 派生クラスでコンストラクターが宣言されていない場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] は、`MyBase.New()` を呼び出す暗黙的なパラメーターなしのコンストラクターを生成しようとします。 引数を指定せずに呼び出すことができる基底クラスにアクセス可能なコンストラクターがない場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では暗黙的なコンストラクターを生成できません。 この場合、必要なコンストラクターが <xref:System.ObsoleteAttribute> 属性でマークされるため、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では呼び出すことができません。  
  
 <xref:System.ObsoleteAttribute> を適用することで、使用されなくなった要素としてすべてのプログラミング要素にマークを付けることができます。 これを行う場合は、属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` に設定できます。`True` に設定した場合、コンパイラは、要素を使用する試行をエラーとして処理します。`False` に設定した場合や既定値の `False` を使用した場合、コンパイラは要素の使用が試行されると警告を発行します。  
  
 既定では、<xref:System.ObsoleteAttribute> の <xref:System.ObsoleteAttribute.IsError%2A> プロパティが `False` であるため、このメッセージは警告となります。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC41001  
  
### このエラーを解決するには  
  
1.  `Sub New` を使用して、派生クラスでコンストラクターを宣言します。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)