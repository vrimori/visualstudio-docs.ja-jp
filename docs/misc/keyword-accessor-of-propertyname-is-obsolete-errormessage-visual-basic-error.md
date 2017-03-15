---
title: "&#39;&lt;propertyname&gt;&#39; の &#39;&lt;keyword&gt;&#39; アクセサーは廃止されています: &#39;&lt;errormessage&gt;&#39; (Visual Basic エラー) | Microsoft Docs"
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
  - "vbc30911"
  - "bc30911"
helpviewer_keywords: 
  - "BC30911"
ms.assetid: b690be0c-4dca-4f79-88ed-4ee3e3f1f90b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;propertyname&gt;&#39; の &#39;&lt;keyword&gt;&#39; アクセサーは廃止されています: &#39;&lt;errormessage&gt;&#39; (Visual Basic エラー)
ステートメントにより、対応するプロシージャが <xref:System.ObsoleteAttribute> 属性およびエラーとして扱うことを示すディレクティブでマークされた、プロパティの読み取りまたは書き込みが試行されます。  
  
 <xref:System.ObsoleteAttribute> を適用することで、使用されなくなった要素としてすべてのプログラミング要素にマークを付けることができます。 これを行う場合は、属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` に設定できます。`True` に設定した場合、コンパイラは、要素を使用する試行をエラーとして処理します。`False` に設定した場合や既定値の `False` を使用した場合、コンパイラは要素の使用が試行されると警告を発行します。  
  
 **エラー ID:** BC30911  
  
### このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、適切なアクションを実行します。  
  
2.  ソース コードの参照で、プロパティ名のスペルが正しいことを確認してください。  
  
3.  このメッセージが生成された方法 \(読み取りまたは書き込み\) で、プロパティにアクセスしないようにします。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)