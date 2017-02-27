---
title: "CA1814: 複数次元の配列ではなくジャグ配列を使用します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
helpviewer_keywords: 
  - "CA1814"
  - "PreferJaggedArraysOverMultidimensional"
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1814: 複数次元の配列ではなくジャグ配列を使用します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|あり|  
  
## 原因  
 メンバーが多次元配列として宣言されています。  
  
## 規則の説明  
 ジャグ配列とは、その要素も配列である配列です。  要素を構成する配列のサイズは異なってもよいため、データ セットによっては無駄な空間が少なくなります。  
  
## 違反の修正方法  
 この規則違反を修正するには、多次元配列をジャグ配列に変更します。  
  
## 警告を抑制する状況  
 多次元配列でも領域が無駄にならない場合は、この規則による警告を抑制します。  
  
## 使用例  
 ジャグ配列と多次元配列の宣言を次の例に示します。  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-cs[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]