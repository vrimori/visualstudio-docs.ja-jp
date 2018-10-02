---
title: 'Ca 2143: 透過的メソッドはセキュリティ確認要求を使用しないでください |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed55d0645e70303f53bbd0d95021d05bb560fe23
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591934"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: 透過的メソッドは、セキュリティ確認要求を使用してはならない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 2143: 透過的メソッドは、セキュリティ要求を使用しないでください](https://docs.microsoft.com/visualstudio/code-quality/ca2143-transparent-methods-should-not-use-security-demands)します。

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 透明の型またはメソッドでマークされた宣言によって、 <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand`オンデマンドまたはメソッドの呼び出し、<xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>メソッド。

## <a name="rule-description"></a>規則の説明
 透過的セキュリティ コードでは、操作のセキュリティ検証を行うことができないため、アクセス許可を要求できません。 透過的セキュリティ コードは、フル アクセス要求を使用して、セキュリティ上の決定を行う必要があります。セーフ クリティカルなコードでは、透過的なコードを使用してフル アクセス要求を行うことはできません。 セキュリティ確認要求などのセキュリティ チェックを実行するコードは、代わりにセーフ クリティカルにする必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 一般に、この規則の違反を修正するを持つメソッドをマーク、<xref:System.Security.SecuritySafeCriticalAttribute>属性。 要求を削除することもできます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 ルールは、透過的メソッドは、宣言型のセキュリティ確認要求するため、次のコードをファイルします。

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>関連項目
 [CA2142: 透過的コードは、LinkDemand を使用して保護されてはならない](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)



