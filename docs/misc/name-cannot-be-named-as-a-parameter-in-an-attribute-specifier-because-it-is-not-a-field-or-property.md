---
title: "&#39;&lt;name&gt;&#39; はフィールドまたはプロパティでないため、属性指定子の中でパラメーターとして名前を指定することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32010"
  - "bc32010"
helpviewer_keywords: 
  - "BC32010"
ms.assetid: bfa68729-71ea-410e-bef1-83a7dab44d2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;name&gt;&#39; はフィールドまたはプロパティでないため、属性指定子の中でパラメーターとして名前を指定することはできません
属性ブロックが、属性の変数でないメンバーを設定しています。 値は、フィールドやプロパティなどの変数のメンバーにのみ割り当てることができます。  
  
 **エラー ID:** BC32010  
  
### このエラーを解決するには  
  
1.  属性名とメンバー名のスペルが正しいことを確認します。  
  
2.  メンバーが変数でない場合は、属性ブロックから引数を削除します。  
  
## 参照  
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)