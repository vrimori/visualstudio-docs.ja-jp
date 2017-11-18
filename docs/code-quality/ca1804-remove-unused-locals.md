---
title: "Ca 1804: 使用されていないローカルを削除する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9217f3109c6ef03de33e444e723caa585d065efb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: 使用されていないローカルを削除します
|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|カテゴリ|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 メソッドはローカル変数を宣言は使用しませんを除く変数可能性のある代入ステートメントの受信者として。 このルールによって、分析のためデバッグ情報と共に、テスト対象のアセンブリを構築する必要あるし、関連付けられているプログラム データベース (.pdb) ファイルを使用する必要があります。  
  
## <a name="rule-description"></a>規則の説明  
 使用されていないローカル変数や不要な引数があると、アセンブリのサイズが大きくなり、パフォーマンスが低下します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するのには、削除するか、ローカル変数を使用します。 C# コンパイラに含まれて[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]未使用のローカル変数を削除時に、`optimize`オプションが有効にします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 変数がコンパイラで生成された場合は、この規則による警告を抑制します。 パフォーマンスとコードの保守が最も重要なのではない場合にも、この規則による警告を抑制するか、ルールを無効に安全です。  
  
## <a name="example"></a>例  
 次の例は、いくつか使用されていないローカル変数を示しています。  
  
 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1809: ローカルを使用しすぎないでください](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: インスタンス化されていない内部クラスを使用しないでください](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: 使用されていないパラメーターをレビューします](../code-quality/ca1801-review-unused-parameters.md)