---
title: "&#39;&lt;mathfunction1&gt;&#39; が宣言されていません | Microsoft Docs"
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
  - "bc30819"
  - "vbc30819"
helpviewer_keywords: 
  - "BC30819"
ms.assetid: 4d30785f-a8fe-438a-846a-8e15ff3f49f5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;mathfunction1&gt;&#39; が宣言されていません
'\<mathfunction1\>' が宣言されていません。 関数は既に System.Math クラスに移動されており、現在は '\<mathfunction2\>' という名前になっています。  
  
 以前のバージョンの [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] に組み込まれていたいくつかの関数は <xref:System.Math?displayProperty=fullName> 名前空間に移動されています。 これにより、これらの機能をより幅広くすべてのプログラミング言語で使用できます。  
  
 **エラー ID:** BC30819  
  
### このエラーを解決するには  
  
-   <xref:System.Math?displayProperty=fullName> で宣言したメソッドを使用します。  
  
## 参照  
 <xref:System.Math>   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/ja-jp/0483590a-6309-449c-a2fa-effa26a03b95)