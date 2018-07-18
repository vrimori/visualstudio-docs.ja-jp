---
title: 'CA1809: ローカルを使用しすぎないでください'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea0d1d27f583e86a62e9c0ff524d9d623253d007
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917341"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: ローカルを使用しすぎないでください
|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メンバーには、64 を超えるローカル変数、一部のコンパイラによって生成された可能性がありますが含まれています。

## <a name="rule-description"></a>規則の説明
 一般的なパフォーマンス最適化と呼ばれますが、メモリ内の代わりにプロセッサのレジスタに値を格納する*のレジスタ格納*値。 共通言語ランタイムでは、enregistration の最大 64 個のローカル変数と見なします。 レジスタではない変数は、スタック上に配置され、操作の前に、レジスタに移動する必要があります。 発生する可能性を許可するすべてのローカル変数はレジスタ格納を 64 個のローカル変数の数を制限します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、64 個のローカル変数を使用する実装をリファクタリングします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パフォーマンスに問題がない場合、この規則による警告を抑制するか、ルールを無効にも安全です。

## <a name="related-rules"></a>関連規則
 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)