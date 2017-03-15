---
title: "&#39;&lt;membername&gt;&#39; は古い形式です: &#39;&lt;errormessage&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30668"
  - "vbc30668"
helpviewer_keywords: 
  - "BC30668"
ms.assetid: 25e5606c-2734-4f42-a2bc-1ad28ec1e892
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membername&gt;&#39; は古い形式です: &#39;&lt;errormessage&gt;&#39;
<xref:System.ObsoleteAttribute> 属性でマークされているクラスまたは構造体にステートメントがアクセスを試行しています。この試行をディレクティブはエラーとして処理します。  
  
 <xref:System.ObsoleteAttribute> を適用することで、使用されなくなった要素としてすべてのプログラミング要素にマークを付けることができます。 これを行う場合は、属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` に設定できます。`True` に設定した場合、コンパイラは、この要素を使用する試行をエラーとして処理します。`False` に設定した場合、または既定値の `False` を使用した場合、コンパイラはこの要素の使用が試行されると、警告を発行します。  
  
 **エラー ID:** BC30668  
  
### このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、適切なアクションを実行します。  
  
2.  ソース コード参照のメンバー名のスペルが正しいことを確認します。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)