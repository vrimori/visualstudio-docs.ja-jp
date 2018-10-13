---
title: ': Ca 1505 メンテナンスできないコード |Microsoft Docs'
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
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d5c333299f323e03a01b121fb18799e9249bcc11
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223289"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: メンテナンスできないコードを使用しないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 型またはメソッドの保守容易性指数が低い値です。

## <a name="rule-description"></a>規則の説明
 保守容易性指数は、次のメトリックを使用して計算されます。 行のコード、プログラムのボリューム、およびサイクロマティック複雑度。 プログラムのボリュームは、型または演算子とオペランドのコードの数に基づいているメソッドの理解の難しさの尺度です。 サイクロマティック複雑度は、型またはメソッドの構造上の複雑さの基準です。 コード メトリックに関する詳細については、[を測定する複雑さとマネージ コードの保守容易性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)します。

 保守性が低いインデックスことを示します型またはメソッドを維持するが困難な可能性が再設計に適した候補となります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この違反を修正するには、型またはメソッドを再設計し、小さくなりより対象を絞った型またはメソッドに分割することをお試しください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 型またはメソッドと見なされます、大きなサイズに関係なく、または、型またはメソッドを分割することはできません、保守性の高いときに、この警告を除外します。

## <a name="see-also"></a>関連項目
 [保守性に関する警告](../code-quality/maintainability-warnings.md)[複雑さとマネージ コードの保守性を測定します。](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



