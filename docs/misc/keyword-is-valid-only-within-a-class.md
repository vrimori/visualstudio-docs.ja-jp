---
title: "&#39;&lt;keyword&gt;&#39; は、クラス内でのみ有効です | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32002"
  - "vbc32002"
helpviewer_keywords: 
  - "BC32002"
ms.assetid: 773d8d50-abb8-4257-83a5-6e017c199d82
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;keyword&gt;&#39; は、クラス内でのみ有効です
`Me` や `MyClass` など、クラスに関連するキーワードがクラス定義外で使用されています。  
  
 **エラー ID:** BC32002  
  
### このエラーを解決するには  
  
-   キーワードを使用するコードがクラス インスタンスに関連する場合は、これをクラスの実装に移動します。  
  
-   キーワードを使用するコードがクラスに適用されない場合は、無効なキーワードを削除します。  
  
## 参照  
 [Me](http://msdn.microsoft.com/ja-jp/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass \- 削除](http://msdn.microsoft.com/ja-jp/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)