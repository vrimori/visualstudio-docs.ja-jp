---
title: "&#39;&lt;typename&gt;&#39; はデリゲート型ではないため、&#39;AddressOf&#39; 式を &#39;&lt;typename&gt;&#39; に変換できません | Microsoft Docs"
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
  - "vbc30581"
  - "bc30581"
helpviewer_keywords: 
  - "BC30581"
ms.assetid: 5db7589a-5456-4b3a-9d6b-93d9157f0484
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; はデリゲート型ではないため、&#39;AddressOf&#39; 式を &#39;&lt;typename&gt;&#39; に変換できません
ステートメントが `AddressOf` 式をデリゲート型ではない型に変換しようとしました。  
  
 `AddressOf` 演算子は、特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。`AddressOf` は、デリゲート コンストラクターのオペランドとして使用するか、コンパイラによってデリゲートの型を決定できるコンテキストで使用することができます。  
  
 **エラー ID:** BC30581  
  
### このエラーを解決するには  
  
-   ターゲットの種類をデリゲート型に変更します。  
  
## 参照  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [ビルド内にありません: デリゲートと AddressOf 演算子](http://msdn.microsoft.com/ja-jp/7b2ed932-8598-4355-b2f7-5cedb23ee86f)