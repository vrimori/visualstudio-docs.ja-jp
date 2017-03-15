---
title: "別のコンストラクターを呼び出している間は、作成中のオブジェクトへの暗黙的な参照は有効ではありません | Microsoft Docs"
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
  - "vbc31096"
  - "bc31096"
helpviewer_keywords: 
  - "BC31096"
ms.assetid: 558a2beb-aa5d-41a8-8655-ad3d16ac8acd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 別のコンストラクターを呼び出している間は、作成中のオブジェクトへの暗黙的な参照は有効ではありません
オブジェクトのコンストラクターによるオブジェクトの構築が完了する前に、そのオブジェクトのメンバーが参照されました。  
  
 **エラー ID:** BC31096  
  
### このエラーを解決するには  
  
-   コンストラクターから別のコンストラクターを呼び出す際には、`MyBase`、`MyClass`、または `Me` を使用しないでください。  
  
## 参照  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NOT IN BUILD: コンストラクターとデストラクターの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)