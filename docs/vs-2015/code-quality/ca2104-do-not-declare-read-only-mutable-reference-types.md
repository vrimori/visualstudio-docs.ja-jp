---
title: 'Ca 2104: 読み取りのみ変更可能な参照型を宣言しません |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 66248e6920c879932204ddb25a40820720adfd84
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877440"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: 読み取り専用の変更可能な参照型を宣言しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 外部から参照できる型に、変更可能な参照型である、外部から参照可能な読み取り専用のフィールドがあります。

## <a name="rule-description"></a>規則の説明
 変更可能な型とは、インスタンス データを変更できる型です。 <xref:System.Text.StringBuilder?displayProperty=fullName>クラスは、変更可能な参照型の例を示します。 クラスのインスタンスの値を変更できるメンバーが含まれています。 変更不可の参照型の例は、<xref:System.String?displayProperty=fullName>クラス。 インスタンス化された後、その値は変化しません。

 読み取り専用修飾子 ([readonly](http://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) c# で[ReadOnly](http://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8)で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]と[const](http://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) C++ で) 参照型のフィールド (C++ でのポインター) により、フィールドを防止参照型の別のインスタンスで置き換えられます。 ただし、修飾子は、参照型を変更できないよう、フィールドのインスタンス データを妨げません。

 読み取り専用配列フィールドはこの規則から除外されますが、代わりに、違反が発生、 [ca 2105: 配列フィールドを読み取ることができませんのみ](../code-quality/ca2105-array-fields-should-not-be-read-only.md)ルール。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、読み取り専用修飾子を削除するか、重大な変更が許容される場合は、変更不可の型でフィールドを置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 フィールドの種類は変更可能なは場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、この規則違反の原因となるフィールド宣言を示します。

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]



