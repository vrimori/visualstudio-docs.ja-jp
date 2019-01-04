---
title: CA2137:透過的メソッドは、検証可能な IL のみを含まなければならない
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76d628b05ae5c0b6ccb8db94a1bf2c09537fd812
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913199"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137:透過的メソッドは、検証可能な IL のみを含まなければならない

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 メソッドに検証できないコードが含まれているか、メソッドから参照渡しで型が返されます。

## <a name="rule-description"></a>規則の説明
 この規則は、透過的セキュリティ コードが、検証できない MSIL (Microsoft Intermediate Language) を実行しようとすると適用されます。 ただし、規則には完全な IL 検証ツールは含まれていないため、代わりにヒューリスティックを使用して、ほとんどの MSIL 検証違反が検出されます。

 特定のコードにだけ検証可能な MSIL が含まれることは、次のように実行します。 [Peverify.exe (PEVerify ツール)](/dotnet/framework/tools/peverify-exe-peverify-tool) 、アセンブリにします。 PEVerify を実行、**透過的/** のみ検証不可能な透過的なメソッドに、エラーの原因となる出力を制限するオプション。 場合、/、透過的なオプションを使用しない、PEVerify では、検証できないコードを含めることができるは重要なメソッドも検証します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するを持つメソッドをマーク、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性、または検証できないコードを削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 この例ではメソッドは、検証できないコードを使用して、マークする必要があります、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]