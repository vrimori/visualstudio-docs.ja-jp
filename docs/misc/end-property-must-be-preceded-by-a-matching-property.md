---
title: "&#39;End Property&#39; の前には、対応する &#39;Property&#39; を指定しなければなりません | Microsoft Docs"
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
  - "vbc30431"
  - "bc30431"
helpviewer_keywords: 
  - "BC30431"
ms.assetid: b1e02d97-b38a-4acf-b351-1726f17a0051
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Property&#39; の前には、対応する &#39;Property&#39; を指定しなければなりません
コード内で一致する `Property` 宣言を先に記述することなく、`End Property` ステートメントを記述しています。  
  
 **エラー ID:** BC30431  
  
### このエラーを解決するには  
  
-   `End Property` ステートメントが余分な場合は、削除します。  
  
-   `Property` プロシージャが不足している場合は、指定します。  
  
-   `End Property` をコード内の適切な場所に移動します。  
  
## 参照  
 [ビルド内にありません: プロパティと Property プロシージャ](http://msdn.microsoft.com/ja-jp/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)