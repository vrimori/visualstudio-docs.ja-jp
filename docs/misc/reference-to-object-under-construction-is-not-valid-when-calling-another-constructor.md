---
title: "別のコンストラクターを呼び出している間は、作成中のオブジェクトへの参照は有効ではありません | Microsoft Docs"
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
  - "bc31095"
  - "vbc31095"
helpviewer_keywords: 
  - "BC31095"
ms.assetid: 68be49f1-e662-45c7-9998-e0006324535d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 別のコンストラクターを呼び出している間は、作成中のオブジェクトへの参照は有効ではありません
オブジェクトのコンストラクターによるオブジェクトの作成が完了する前に、そのオブジェクトのメンバーが参照されました。  
  
 **エラー ID:** BC31095  
  
### このエラーを解決するには  
  
-   コンストラクターから別のコンストラクターを呼び出す際には、`MyBase`、`MyClass`、または `Me` を使用しないでください。  
  
## 参照  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [ビルド内にありません: コンストラクタとデストラクタの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)