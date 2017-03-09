---
title: "参照されたオブジェクトには値 &#39;Nothing&#39; が指定されています | Microsoft Docs"
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
  - "bc30760"
  - "vbc30760"
helpviewer_keywords: 
  - "BC30760"
ms.assetid: 7e792fd8-2880-402b-a908-c89e5b028300
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 参照されたオブジェクトには値 &#39;Nothing&#39; が指定されています
使用しているオブジェクトに値 `Nothing` がありますが、使用可能な値が必要です。`Nothing` はオブジェクトには値がないことを示す値であり、その理由は、オブジェクトに値が割り当てられなかったか、値 `Nothing` が割り当てられたことです。  
  
 **エラー ID:** BC30760  
  
### このエラーを解決するには  
  
1.  エラーが発生したプロシージャのスコープ内でオブジェクトを宣言していることを確認します。  
  
2.  オブジェクトの値を設定していることを確認します。  
  
    > [!NOTE]
    >  値 `Nothing` は 0 とも空の文字列とも同じではありません。`IsNothing` を使用して、オブジェクトに値 `Nothing` が含まれているかどうかを確認できます。  
  
## 参照  
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [ビルド内にありません: IsNothing 関数](http://msdn.microsoft.com/ja-jp/5b2a4626-e6a9-49d1-b9b1-fcc6a1302319)