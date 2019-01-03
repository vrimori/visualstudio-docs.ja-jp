---
title: CA2207:値型のスタティック フィールドのインラインを初期化します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee4ffd51eef5b8a4f0523dd2356d4e0bdb29b945
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869161"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207:値型のスタティック フィールドのインラインを初期化します

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 値型では、明示的な静的コンス トラクターを宣言します。

## <a name="rule-description"></a>規則の説明
 値型が宣言されている場合、すべての値型フィールドが 0 に設定され、すべての参照型フィールドに設定は、既定の初期化が行われる`null`(`Nothing` Visual Basic で)。 明示的な静的コンス トラクターを実行して、インスタンス コンス トラクターにのみ保証されます。 または、型の静的メンバーが呼び出されます。 そのため、インスタンス コンス トラクターを呼び出さずに、型が作成される場合、静的コンス トラクターを実行する保証されません。

 C# および Visual Basic のコンパイラが追加するかどうかは、すべての静的データが初期化されたインラインと明示的な静的コンス トラクターが宣言されていない、 `beforefieldinit` MSIL クラスの定義にフラグ。 コンパイラでは、静的な初期化コードを含むプライベート静的コンス トラクターも追加します。 このプライベート静的コンス トラクター、型の静的フィールドにアクセスする前に実行することが保証されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 解決するには、は、この規則違反は、宣言されていて、静的コンス トラクターを削除するときに、すべての静的データを初期化します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="related-rules"></a>関連するルール
 [CA 1810:参照型の静的フィールドのインラインを初期化します](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)