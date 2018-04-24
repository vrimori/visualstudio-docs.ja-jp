---
title: 'CA1301: アクセラレータが重複しないようにします'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 0a323ce01201dd4a3650d6da0ddde8edfeea0512
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: アクセラレータが重複しないようにします
|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 型拡張<xref:System.Windows.Forms.Control?displayProperty=fullName>リソース ファイルに格納されている同じアクセス キーを持つ 2 つ以上の最上位レベルのコントロールが含まれています。

## <a name="rule-description"></a>規則の説明
 Alt キーを使用するアクセス キー (アクセラレータとも呼ばれます) によって、キーボードからコントロールにアクセスできます。 アクセス キーの重複したコントロールがあると、アクセス キーの動作は不明確になります。 ユーザーをアクセス キーを使用して目的のコントロールにアクセスすることができない可能性があり、なっているもの以外のコントロールを有効にすることがあります。

 このルールの現在の実装では、メニュー項目を無視します。 ただし、同じサブメニューのメニュー項目では、同じアクセス キーの必要はありません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、すべてのコントロールの一意のアクセス キーを定義します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例は、最小限のと同じアクセス キーを持つ 2 つのコントロールを含むフォームを示しています。 キーが示されていません。 リソース ファイルに格納されています。ただし、その値は、コメントに表示されます。 out`checkBox.Text`行です。 重複するアクセラレータの動作を交換することで調べることができます、`checkBox.Text`対応コメント アウトすると行です。 ただし、ここでは、例では、生成されません警告ルールから。

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>関連項目
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [デスクトップ アプリでのリソース](/dotnet/framework/resources/index)