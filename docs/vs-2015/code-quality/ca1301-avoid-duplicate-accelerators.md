---
title: ': Ca 1301 アクセラレータが重複しない |Microsoft Docs'
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
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e0a7f821f11a86b0ce9bf12708df483a6ae071a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49233247"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: アクセラレータが重複しないようにします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 型拡張<xref:System.Windows.Forms.Control?displayProperty=fullName>リソース ファイルに格納されている同じアクセス キーを持つ 2 つ以上の最上位レベルのコントロールが含まれています。

## <a name="rule-description"></a>規則の説明
 Alt キーを使用するアクセス キー (アクセラレータとも呼ばれます) によって、キーボードからコントロールにアクセスできます。 アクセス キーの重複したコントロールがあると、アクセス キーの動作は不明確になります。 ユーザーは、アクセス キーを使用して目的のコントロールにアクセスできない可能性があり、想定されているもの以外のコントロールが有効になっています。

 このルールの現在の実装では、メニュー項目は無視されます。 ただし、同じサブメニューのメニュー項目では、同じアクセス キーは必要ありません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、すべてのコントロールの一意のアクセス キーを定義します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、同じアクセス キーを持つ 2 つのコントロールが含まれた最小限のフォームを示します。 キーが示されていません。 リソース ファイルに格納されます。ただし、その値は、コメント付きで表示されます。 out`checkBox.Text`行。 重複するアクセラレータの動作を交換することで調べることができます、`checkBox.Text`のコメント アウトされた対応する行。 ただし、ここでは、例では、生成されません警告ルールから。

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>関連項目
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [デスクトップ アプリでのリソース](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



