---
title: 'Ca 2140: 透過的コードはセキュリティ上重要な項目を参照する必要がありますされません |Microsoft Docs'
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
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fb6c01fc281384aec28ae46dbb1466686626df8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892117"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: 透過的コードは、セキュリティ上重要な項目を参照してはならない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 透過的なメソッド:

-   セキュリティの重要なセキュリティ例外の種類を処理します。

-   セキュリティ上重要な型としてマークされているパラメーターがあります。

-   セキュリティの重要な制約を持つジェネリック パラメーターします。

-   セキュリティ上重要な型のローカル変数を持つ

-   重要なセキュリティとしてマークされている型を参照します。

-   重要なセキュリティとしてマークされているメソッドを呼び出します

-   重要なセキュリティとしてマークされているフィールドを参照します。

-   重要なセキュリティとしてマークされている型を返します

## <a name="rule-description"></a>規則の説明
 マークされているコード要素、<xref:System.Security.SecurityCriticalAttribute>属性は、セキュリティ クリティカルです。 透過的なメソッドでセキュリティ上重要な要素を使用することはできません。 透過的な型がセキュリティ クリティカルな型を使用しようとしたかどうか、 <xref:System.TypeAccessException>、 <xref:System.MethodAccessException> 、または<xref:System.FieldAccessException>が発生します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、次のいずれかの操作を行います。

-   セキュリティ クリティカルなコードを使用するコード要素をマーク、<xref:System.Security.SecurityCriticalAttribute>属性

     \- または -

-   削除、<xref:System.Security.SecurityCriticalAttribute>から重要なセキュリティとしてマークされて、代わりにそれらをマークするコード要素、属性、<xref:System.Security.SecuritySafeCriticalAttribute>または<xref:System.Security.SecurityTransparentAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例については、透過的メソッドは、セキュリティの重要なジェネリック コレクション、セキュリティ クリティカル フィールド、およびセキュリティの重要なメソッドを参照しようとします。

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>関連項目
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>



