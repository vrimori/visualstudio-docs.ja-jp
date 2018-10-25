---
title: 'CA2142: 透過的コードは、LinkDemand を使用して保護されてはならない'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ce7243630179aede0ce20aba998f6cb5eed0100
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887168"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: 透過的コードは、LinkDemand を使用して保護されてはならない

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 透過的なメソッドが必要です、<xref:System.Security.Permissions.SecurityAction>またはその他のセキュリティ確認を要求します。

## <a name="rule-description"></a>規則の説明
 この規則は、それらにアクセスするために LinkDemands を要求する透過的メソッドに対して適用されます。 透過的セキュリティ コードでは、操作のセキュリティ検証を行うことができないため、アクセス許可を要求できません。 透過的メソッドは、セキュリティに中立的になっている、ので、行うことができません、セキュリティ上の決定します。 さらに、セキュリティ上の決定を行う、セーフ クリティカル コードは透過的なコードをこのような意思決定を行った以前に依存しない必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、透過的メソッドに対してリンク確認要求を削除するかを持つメソッドをマーク<xref:System.Security.SecuritySafeCriticalAttribute>セキュリティ要求など、セキュリティを実行する場合、属性を確認します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、規則は、メソッドのメソッドは透過的であり、LinkDemand でマークされたため、<xref:System.Security.PermissionSet>を格納している、<xref:System.Security.Permissions.SecurityAction>します。

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

 この規則による警告は抑制しないでください。