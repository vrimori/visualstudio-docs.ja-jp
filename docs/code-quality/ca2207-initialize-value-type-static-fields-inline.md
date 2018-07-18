---
title: 'CA2207: 値型の静的フィールドのインラインを初期化します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 883e5d842346a0821b54b2b4eacad3cbc92028b6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917687"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: 値型の静的フィールドのインラインを初期化します
|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 値型では、明示的な静的コンス トラクターを宣言します。

## <a name="rule-description"></a>規則の説明
 値型が宣言されると、値型のすべてのフィールドが 0 に設定されて、すべての参照型のフィールドを設定する既定の初期化が行われる`null`(`Nothing` Visual Basic で)。 明示的な静的コンス トラクターは、インスタンス コンス トラクターの前に実行することが保証のみまたは型の静的メンバーが呼び出されます。 そのため、インスタンス コンス トラクターを呼び出さずに、型を作成する場合、静的コンス トラクターを実行する保証されません。

 すべての静的データはインラインで初期化し、明示的な静的コンス トラクターが宣言されていない、c# および Visual Basic コンパイラは追加、`beforefieldinit`フラグを MSIL クラス定義です。 コンパイラでは、静的な初期化コードを含むプライベート静的コンス トラクターも追加します。 このプライベート静的コンス トラクターは、型の静的フィールドは、前に実行することが保証します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 修正は、この規則の違反は、宣言されていて、静的コンス トラクターを削除するときに、静的データをすべてを初期化します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="related-rules"></a>関連規則
 [CA1810: 参照型の静的フィールドをインラインで初期化します](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)