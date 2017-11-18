---
title: "Ca 2140: 透過的なコードはセキュリティ上重要な項目を参照する必要があります |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
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
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e11167ba35baf8802709d0d65b9b4045ede25126
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: 透過的コードは、セキュリティ上重要な項目を参照してはならない
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
 マークされているコード要素、<xref:System.Security.SecurityCriticalAttribute>属性はセキュリティ クリティカルです。 透過的なメソッドでセキュリティ上重要な要素を使用することはできません。 透過的な型がセキュリティ クリティカルな型を使用しようとしたかどうか、 <xref:System.TypeAccessException>、 <xref:System.MethodAccessException> 、または<xref:System.FieldAccessException>が発生します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、次のいずれかの操作を行います。  
  
-   使用してセキュリティ クリティカルなコードを使用するコード要素をマーク、<xref:System.Security.SecurityCriticalAttribute>属性  
  
     \- または  
  
-   削除、<xref:System.Security.SecurityCriticalAttribute>重要なセキュリティとマークされて、代わりにそれらをマークするコード要素から属性を<xref:System.Security.SecuritySafeCriticalAttribute>または<xref:System.Security.SecurityTransparentAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例については、透過的メソッドは、セキュリティ クリティカルなジェネリック コレクション、セキュリティ クリティカルなフィールド、およびセキュリティ上重要なメソッドを参照しようとします。  
  
 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>