---
title: 'Ca 2213: 破棄可能なフィールドを破棄する必要があります |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f9921ee2640c25b19d02aabb140032918c2133b5
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589269"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: 破棄可能なフィールドは破棄されなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 2213: 破棄可能なフィールドを破棄する必要があります](https://docs.microsoft.com/visualstudio/code-quality/ca2213-disposable-fields-should-be-disposed)します。

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 実装する型<xref:System.IDisposable?displayProperty=fullName>も実装する型のフィールドを宣言<xref:System.IDisposable>します。 <xref:System.IDisposable.Dispose%2A>フィールドのメソッドを呼び出さない、<xref:System.IDisposable.Dispose%2A>宣言型のメソッド。

## <a name="rule-description"></a>規則の説明
 型はすべて、アンマネージ リソースの破棄を担当これは、実装することによって実現<xref:System.IDisposable>します。 このルールは、破棄可能な型かどうかを確認します`T`フィールドを宣言して`F`破棄可能な型のインスタンスである`FT`します。 各フィールドの`F`、ルールの呼び出しを検索しようとしました。`FT.Dispose`します。 ルールによって呼び出されるメソッドを検索する`T.Dispose`、および下位のレベル (によって呼び出されるメソッドによって呼び出されるメソッド`FT.Dispose`)。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するに<xref:System.IDisposable.Dispose%2A>を実装する型のフィールドで<xref:System.IDisposable>を割り当て、そのフィールドによって保持されているアンマネージ リソースを解放します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 いないの責任者は、フィールドによって保持されているリソースを解放する場合、または場合にこの規則による警告を抑制するのには安全では、呼び出し<xref:System.IDisposable.Dispose%2A>ルール チェックよりも詳細な呼び出し元のレベルで発生します。

## <a name="example"></a>例
 次の例は、型`TypeA`を実装する<xref:System.IDisposable>(`FT` previosu ディスカッションで)。

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>例
 次の例は、型`TypeB`フィールドを宣言することでこの規則に違反する`aFieldOfADisposableType`(`F`上記の説明で)、破棄可能な型として (`TypeA`) を呼び出さない<xref:System.IDisposable.Dispose%2A>フィールド。 `TypeB` 対応する`T`で、前に説明します。

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>関連項目
 <xref:System.IDisposable?displayProperty=fullName> [Dispose パターン](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



