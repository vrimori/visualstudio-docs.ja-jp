---
title: "型 &#39;&lt;typename&gt;&#39; は &#39;MustInherit&#39; として宣言されていて作成することができないので、&#39;AddressOf&#39; 式を &#39;&lt;typename&gt;&#39; に変換することはできません | Microsoft Docs"
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
  - "vbc30939"
  - "bc30939"
helpviewer_keywords: 
  - "BC30939"
ms.assetid: e8edef15-0df5-46d7-aba6-89e26a2aa506
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;typename&gt;&#39; は &#39;MustInherit&#39; として宣言されていて作成することができないので、&#39;AddressOf&#39; 式を &#39;&lt;typename&gt;&#39; に変換することはできません
ステートメントが `AddressOf` 式を型に変換しようとしていますが、その型は基底クラスにすることのみができ、インスタンスの作成には使用できません。  
  
 `AddressOf` 演算子は、特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。  
  
 **エラー ID:** BC30939  
  
### このエラーを解決するには  
  
-   `AddressOf` 式を、特定のデリゲート型に代入します。  
  
## 参照  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [ビルド内にありません: デリゲートと AddressOf 演算子](http://msdn.microsoft.com/ja-jp/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegates](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)