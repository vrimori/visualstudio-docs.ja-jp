---
title: "&#39;&lt;keyword&gt;&#39; キーワードは、継承されたメンバーをオーバーロードするために使用されます。&#39;Sub New&#39; をオーバーロードするときには &#39;&lt;keyword&gt;&#39; を使用しないでください | Microsoft Docs"
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
  - "vbc32040"
  - "bc32040"
helpviewer_keywords: 
  - "BC32040"
ms.assetid: 39e6ee0d-b8a0-498e-bdaf-a4ceb13892fe
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;keyword&gt;&#39; キーワードは、継承されたメンバーをオーバーロードするために使用されます。&#39;Sub New&#39; をオーバーロードするときには &#39;&lt;keyword&gt;&#39; を使用しないでください
コンストラクターが `Overloads` キーワードを使用して宣言されています。  
  
 Visual Basic は、コンストラクターの継承またはオーバーロードをサポートしていません。  
  
 **エラー ID:** BC32040  
  
### このエラーを解決するには  
  
-   すべてのコンストラクターの宣言から `Overloads` キーワードを削除します。  
  
## 参照  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [ビルド内にありません: コンストラクタとデストラクタの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)