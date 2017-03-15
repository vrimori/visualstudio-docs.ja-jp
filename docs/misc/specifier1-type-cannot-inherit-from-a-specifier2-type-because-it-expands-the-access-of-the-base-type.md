---
title: "ベース &lt;type&gt; のアクセスを展開しているため、&lt;specifier1&gt; &lt;type&gt; は &lt;specifier2&gt; &lt;type&gt; から継承できません | Microsoft Docs"
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
  - "bc30509"
  - "vbc30509"
helpviewer_keywords: 
  - "BC30509"
ms.assetid: 53594d6e-5e6d-463d-aa68-e2d41e152da7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ベース &lt;type&gt; のアクセスを展開しているため、&lt;specifier1&gt; &lt;type&gt; は &lt;specifier2&gt; &lt;type&gt; から継承できません
`Private` または `Friend` に指定された基底クラスからパブリック クラスを継承しようとしました。  
  
 **エラー ID:** BC30509  
  
### このエラーを解決するには  
  
-   基底クラスを `Public` と宣言するか、継承するクラスを `Private` または `Friend` と宣言します。  
  
## 参照  
 [NOT IN BUILD: Visual Basic の継承](http://msdn.microsoft.com/ja-jp/e5e6e240-ed31-4657-820c-079b7c79313c)