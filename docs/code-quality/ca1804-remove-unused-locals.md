---
title: 'CA1804: 使用されていないローカルを削除します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b1846c1b8d9173db6d1f4b5acd0544fd601da67a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545464"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: 使用されていないローカルを削除します

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メソッドでローカル変数を宣言も使わないを除く変数可能性があります、代入ステートメントの受信者として。 このルールによって、分析するためには、デバッグ情報のテスト対象のアセンブリをビルドする必要があり、関連付けられているプログラム データベース (.pdb) ファイルは、使用可能なである必要があります。

## <a name="rule-description"></a>規則の説明
 使用されていないローカル変数や不要な引数があると、アセンブリのサイズが大きくなり、パフォーマンスが低下します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、削除するか、ローカル変数を使用します。 C# コンパイラに含まれるに注意してください。[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]未使用のローカル変数を削除します。 ときに、`optimize`オプションを有効にします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 変数がコンパイラで生成された場合は、この規則による警告を抑制します。 パフォーマンスとコードのメンテナンスが主な懸念事項ではない場合にも、この規則による警告を抑制するか、ルールを無効にするには安全です。

## <a name="example"></a>例
 次の例では、未使用のローカル変数をいくつかを示します。

 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1809: ローカルを使用しすぎないでください](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: インスタンス化されていない内部クラスを使用しないでください](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: 使用されていないパラメーターをレビューします](../code-quality/ca1801-review-unused-parameters.md)