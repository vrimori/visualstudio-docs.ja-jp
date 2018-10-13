---
title: 'Ca 2130: セキュリティ上重要な定数を透明にする必要があります |Microsoft Docs'
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
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0e8e76469a60a8b14157b840b9b050519b9a6ac4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186582"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: セキュリティ上重要な定数は透過的である必要がある
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 定数フィールドまたは列挙体のメンバーが付いて、<xref:System.Security.SecurityCriticalAttribute>します。

## <a name="rule-description"></a>規則の説明
 実行時に検索の必要がない値がコンパイラのインライン定数に設定されているため、定数値に対して透過性は適用されません。 透過的なコードからは定数にアクセスできないとコード レビューアーが考えることがないよう、定数フィールドは透過的セキュリティなフィールドとして定義する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、フィールドまたは値から SecurityCritical 属性を削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、列挙値で`EnumWithCriticalValues.CriticalEnumValue`と定数`CriticalConstant`この警告が通知されます。 問題を解決するには、削除、[`SecurityCritical`] を透明にセキュリティ属性。

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]



