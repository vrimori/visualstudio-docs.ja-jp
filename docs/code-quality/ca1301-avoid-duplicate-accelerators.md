---
title: CA1301:重複するアクセラレータを使用しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d20ec103b2861fbdb80d45b82135686c26b91c9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944987"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301:重複するアクセラレータを使用しません

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 型拡張<xref:System.Windows.Forms.Control?displayProperty=fullName>リソース ファイルに格納されている同じアクセス キーを持つ 2 つまたは複数のトップレベル コントロールが含まれています。

## <a name="rule-description"></a>規則の説明

アクセス キーをアクセラレータとも呼ばれますが、使用してキーボード コントロールへのアクセスを可能、 **Alt**キー。 複数のコントロールと同じアクセス キーがある、アクセス キーの動作は定義されていません。 ユーザーは、アクセス キーを使用して目的のコントロールにアクセスできない可能性があり、想定されているもの以外のコントロールが有効になっています。

このルールの現在の実装では、メニュー項目は無視されます。 ただし、同じサブメニューのメニュー項目では、同じアクセス キーは必要ありません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、すべてのコントロールの一意のアクセス キーを定義します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、同じアクセス キーを持つ 2 つのコントロールが含まれた最小限のフォームを示します。 キーは、示されていませんが、リソース ファイルに格納されます。 ただし、その値は、コメント付きで表示されます。 out`checkBox.Text`行。 重複するアクセラレータの動作を交換することで調べることができます、`checkBox.Text`のコメント アウトされた対応する行。 ただし、ここでは、例では、生成されません警告ルールから。

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>関連項目

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [デスクトップ アプリケーションのリソース](/dotnet/framework/resources/index)