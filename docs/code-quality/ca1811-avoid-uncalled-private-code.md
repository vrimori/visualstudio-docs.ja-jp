---
title: CA1811:呼び出されていないプライベート コードを使用しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fca30671616dbe1e9d1c3468420d4526aa02250
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975154"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811:呼び出されていないプライベート コードを使用しません

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 プライベートまたは内部 (アセンブリ レベル) メンバーは、アセンブリが呼び出し元がありません。 は、共通言語ランタイムによって呼び出されません、およびによってデリゲートは呼び出されません。 このルールでは、次のメンバーはチェックされません。

- 明示的なインターフェイスのメンバー。

- 静的コンス トラクター。

- シリアル化コンス トラクター。

- マークされたメソッド<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>または<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>します。

- オーバーライドするメンバー。

## <a name="rule-description"></a>規則の説明
 このルールは、偽陽性のエントリ ポイントが発生した場合は現在、規則のロジックを識別しないレポートできます。 また、コンパイラは、アセンブリに noncallable コードを生成する可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、noncallable コードを削除するか、それを呼び出すコードを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 このルールから警告を抑制しても安全です。

## <a name="related-rules"></a>関連するルール
 [CA1812:インスタンス化されていない内部クラスを回避します。](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA 1801:未使用のパラメーターをレビューします](../code-quality/ca1801-review-unused-parameters.md)

 [CA 1804:使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)