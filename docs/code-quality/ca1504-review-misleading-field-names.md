---
title: 'CA1504: 紛らわしいフィールド名を確認します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1457390b523af45b5e3b23a3420cba830f45cee5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915083"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: 紛らわしいフィールド名を確認します
|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 インスタンス フィールドの名前が「s _」またはの名前で始まる、 `static` (`Shared`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) フィールドが「m _」で開始します。

## <a name="rule-description"></a>規則の説明
 「S _」で始まるフィールド名は、多数のユーザーによる静的データに関連付けられます。 同様に、「m _」で始まるフィールド名は、インスタンス (メンバー) のデータに関連付けられます。 保守が簡単なコードは、名は、一般的に使用される規則に従う必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、適切なプレフィックスを使用してフィールドを変更します。 または、追加または削除して、現在のサフィックスに合致するフィールドを変更、`static`修飾子です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。