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
ms.openlocfilehash: e8769d7dd30152523d60f2f0fa117e0179d6c6b0
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545451"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: 紛らわしいフィールド名を確認します
|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 インスタンス フィールドの名前の名前または「s _」で始まり、 `static` (`Shared`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) フィールドが「m _」で開始します。

## <a name="rule-description"></a>規則の説明
 「S _」で始まるフィールド名は、多くのユーザーによって静的データに関連付けられます。 同様に、「m _」で始まるフィールド名は、インスタンス (メンバー) のデータに関連付けられます。 保守が簡単なコードは、名は、一般的に使用される規則に従う必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、適切なプレフィックスを使用して、フィールド名を変更します。 または、追加または削除して、現在のサフィックスと一致するフィールドを変更、`static`修飾子。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。