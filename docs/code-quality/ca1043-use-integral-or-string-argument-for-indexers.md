---
title: "Ca 1043: インデクサーには整数または文字列引数を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a75e3cc167f98763cfc0a1747b48e69987a9610b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: インデクサーには整数または文字列引数を使用します
|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクト型には、以外のインデックスの種類を使用して、パブリックまたはプロテクトのインデクサーが含まれています。 <xref:System.Int32?displayProperty=fullName>、 <xref:System.Int64?displayProperty=fullName>、 <xref:System.Object?displayProperty=fullName>、または<xref:System.String?displayProperty=fullName>です。  
  
## <a name="rule-description"></a>規則の説明  
 インデクサー、つまり、インデックス付きプロパティは、インデックスに整数型または文字列型を使用する必要があります。 これらの型は、通常のデータ構造のインデックス作成に使用され、ライブラリの使いやすさを向上します。 使用、<xref:System.Object>型は、デザイン時に特定の整数型または文字列型を指定することはできない場合に限定する必要があります。 設計では、インデックスの他の種類が必要とする場合は、型の論理データ ストアを表しているかどうかを再確認します。 論理データ ストアを表さない場合は、メソッドを使用します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、整数または文字列型では、インデックスを変更またはインデクサーではなく、メソッドを使用します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 非標準のインデクサーの必要性を慎重に検討した後にのみこの規則による警告は抑制されます。  
  
## <a name="example"></a>例  
 次の例では、インデクサーを使用する、<xref:System.Int32>インデックス。  
  
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1023: インデクサーを多次元にすることはできません](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: 適切な場所にプロパティを使用します](../code-quality/ca1024-use-properties-where-appropriate.md)