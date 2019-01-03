---
title: CA1401:P-Invoke は参照可能になりません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e52140f07cb72eca62a1a52a01ae37e3e6a53382
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930316"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401:P/Invoke は参照可能であることはできません

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型の public または protected のメソッドには、<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性 (によって実装されることも、`Declare`キーワード[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。

## <a name="rule-description"></a>規則の説明
 マークされているメソッド、<xref:System.Runtime.InteropServices.DllImportAttribute>属性 (またはを使用して定義されているメソッド、`Declare`キーワード[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) プラットフォーム呼び出しサービスを使用して、アンマネージ コードにアクセスします。 このようなメソッドは公開しないでください。 プライベートまたは内部には、これらのメソッドを保持することで呼び出し元がそれ以外の場合、呼び出しできなかったアンマネージ Api にアクセスできるようにしてセキュリティを侵害するライブラリを使用できないことを確認します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メソッドのアクセス レベルを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、この規則に違反するメソッドを宣言します。

 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]