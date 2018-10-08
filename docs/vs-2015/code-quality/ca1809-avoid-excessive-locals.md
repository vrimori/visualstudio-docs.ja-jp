---
title: 'CA1809: 過剰なローカルの回避 |Microsoft Docs'
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
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c41836e2a7e7e5530d83ff0eaf854b88de42f38f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589744"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: ローカルを使用しすぎないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1809: 過剰なローカル](https://docs.microsoft.com/visualstudio/code-quality/ca1809-avoid-excessive-locals)します。

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メンバーには、64 を超えるローカル変数、一部のコンパイラによって生成された可能性がありますが含まれています。

## <a name="rule-description"></a>規則の説明
 一般的なパフォーマンスの最適化と呼ばれるメモリ内の代わりにプロセッサのレジスタに値を格納する、*レジスタ格納*値。 共通言語ランタイムでは、最大 64 個のローカル変数の enregistration と見なします。 レジスタではない変数をスタックに配置され、操作する前に、レジスタに移動する必要があります。 可能性を許可するすべてのローカル変数がレジスタ格納、64 をローカル変数の数を制限します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、64 個のローカル変数を使用する実装をリファクタリングします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パフォーマンスに問題がない場合、この規則による警告を抑制するか、ルールを無効にするには安全です。

## <a name="related-rules"></a>関連規則
 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)



