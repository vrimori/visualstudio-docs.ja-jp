---
title: 'Ca 1401: P を呼び出す必要がありますになりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2aaadb0570e47e5ef41614925c20f8dc30f1620
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invoke は参照可能になりません
|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型のパブリックまたはプロテクト メソッドには、<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性 (実装しても、`Declare`キーワード[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。

## <a name="rule-description"></a>規則の説明
 マークされたメソッド、<xref:System.Runtime.InteropServices.DllImportAttribute>属性 (またはメソッドを使用して定義されている、`Declare`キーワード[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) プラットフォーム呼び出しサービスを使用してアンマネージ コードにアクセスします。 このようなメソッドは公開しないでください。 プライベートまたは内部には、これらのメソッドを保持することでの呼び出し元のそれ以外の場合、呼び出しできなかったアンマネージ Api へのアクセスを許可することでセキュリティを侵害するライブラリを使用できないことを確認します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メソッドのアクセス レベルを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、この規則に違反するメソッドを宣言します。

 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]