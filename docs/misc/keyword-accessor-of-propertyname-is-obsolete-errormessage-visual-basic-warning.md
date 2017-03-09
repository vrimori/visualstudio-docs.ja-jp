---
title: "&#39;&lt;propertyname&gt;&#39; の &#39;&lt;keyword&gt;&#39; アクセサーは古い形式です: &#39;&lt;errormessage&gt;&#39; (Visual Basic 警告) | Microsoft Docs"
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
  - "bc40019"
  - "vbc40019"
helpviewer_keywords: 
  - "BC40019"
ms.assetid: 57d00655-1837-4605-a5e9-1ae5b6935f51
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;propertyname&gt;&#39; の &#39;&lt;keyword&gt;&#39; アクセサーは古い形式です: &#39;&lt;errormessage&gt;&#39; (Visual Basic 警告)
ステートメントがプロパティの読み取りまたは書き込みをしようとしていますが、対応するプロシージャはこのプロパティに対し、<xref:System.ObsoleteAttribute> 属性と、これを警告として扱うよう指定するディレクティブでマークを付けています。  
  
 どのプログラミング要素でも、<xref:System.ObsoleteAttribute> を適用すれば、もう使用しなくなったものとしてマークを付けることができます。 これを行う場合は、属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` に設定できます。`True` に設定した場合、要素を使用しようとするとコンパイラはエラーとして処理します。`False` に設定した場合や既定値の `False` を使用した場合、要素を使用しようとするとコンパイラは警告を発行します。  
  
 既定では、<xref:System.ObsoleteAttribute> の <xref:System.ObsoleteAttribute.IsError%2A> プロパティが `False` であるため、メッセージは警告となります。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40019  
  
### このエラーを解決するには  
  
1.  引用されているエラー メッセージを確認し、適切な処理を行います。  
  
2.  ソース コードの参照で、プロパティ名のスペルが正しいことをご確認ください。  
  
3.  このメッセージの原因となった方法 \(読み取りか書き込み\) でプロパティにアクセスしないようにします。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)