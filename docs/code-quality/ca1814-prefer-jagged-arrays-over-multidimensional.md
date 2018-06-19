---
title: 'CA1814: 複数次元の配列ではなくジャグ配列を使用します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cbcf3cc6167cc98cb61380aa1ac54af5a291eb09
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915745"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: 複数次元の配列ではなくジャグ配列を使用します
|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 メンバーは、多次元配列として宣言されています。

## <a name="rule-description"></a>規則の説明
 ジャグ配列とは、その要素も配列である配列です。 要素を構成する配列のサイズは異なってもよいため、データ セットによっては無駄な空間が少なくなります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、ジャグ配列を多次元配列を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 多次元配列領域が無駄にならない場合は、この規則による警告を抑制します。

## <a name="example"></a>例
 次の例は、ジャグ配列と多次元配列の宣言を示しています。

 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]