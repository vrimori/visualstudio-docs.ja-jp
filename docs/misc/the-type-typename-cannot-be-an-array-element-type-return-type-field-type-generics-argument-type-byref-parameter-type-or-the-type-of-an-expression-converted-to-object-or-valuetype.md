---
title: "型 &#39;&lt;typename&gt;&#39; は、配列要素の型、戻り値の型、フィールドの型、汎用引数の型、&#39;ByRef&#39; パラメーターの型、または &#39;Object&#39; または &#39;ValueType&#39; に変換された式の型にすることはできません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31396"
  - "BC31396"
helpviewer_keywords: 
  - "BC31396"
ms.assetid: 56998a2c-a705-482e-87ee-5eff707f8a48
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;typename&gt;&#39; は、配列要素の型、戻り値の型、フィールドの型、汎用引数の型、&#39;ByRef&#39; パラメーターの型、または &#39;Object&#39; または &#39;ValueType&#39; に変換された式の型にすることはできません
変数、プロシージャのパラメーター、型パラメーター、関数の戻り値、または制限された型を持つ配列を式が宣言しています。  
  
 共通言語ランタイム \(CLR\) は、特別な言語でしかサポートしない特定の型を公開しています。これらの型をアプリケーション内でデータ型として使用することはできません。 これらの型には、<xref:System.ArgIterator>、<xref:System.RuntimeArgumentHandle>、<xref:System.TypedReference> の構造体があります。  
  
 **エラー ID:** BC31396  
  
### このエラーを解決するには  
  
-   制限された構造体を宣言されたデータ型として使用しないでください。  
  
## 参照  
 <xref:System.ArgIterator>   
 <xref:System.RuntimeArgumentHandle>   
 <xref:System.TypedReference>