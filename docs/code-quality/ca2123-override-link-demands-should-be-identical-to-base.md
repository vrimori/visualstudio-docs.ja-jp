---
title: 'CA2123: オーバーライドのリンク確認要求は基本と同様にします'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebb37743f9259390aba400a5d89d24b5f41a0d49
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546981"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: オーバーライドのリンク確認要求は基本と同様にします

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型の public または protected のメソッドのメソッドをオーバーライドまたはインターフェイスを実装し、同じではありません[リンク確認要求](/dotnet/framework/misc/link-demands)インターフェイスまたは仮想メソッドとします。

## <a name="rule-description"></a>規則の説明
 この規則は、メソッドをその基本メソッド (別の型のインターフェイスまたは仮想メソッド) とマッチングし、それぞれについてリンク確認要求を比較します。 メソッドまたは基本メソッドのいずれかがリンク確認要求し、もう一方にない場合は、違反が報告されます。

 この規則に違反すると、悪意のある呼び出し元は、保護されていないメソッドを呼び出すことによって単なるリンク確認要求をバイパスできます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メソッドをオーバーライドまたは実装する同じリンク確認要求を適用します。 それができない場合は、完全な要求を持つメソッドをマークまたは属性をすべて削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、このルールのさまざまな違反を示します。

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]

## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)
- [リンク確認要求](/dotnet/framework/misc/link-demands)