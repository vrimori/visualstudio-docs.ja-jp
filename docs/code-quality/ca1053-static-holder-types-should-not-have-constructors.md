---
title: 'CA1053: スタティック ホルダー型にはコンストラクターを含めません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7f99804abeac1c9f536c94c542f6e031bf16ec6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31896593"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: スタティック ホルダー型にはコンストラクターを含めません
|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型または入れ子になったパブリック型で、静的なメンバーのみが宣言されています。また、パブリックまたはプロテクトの既定のコンストラクターが含まれます。

## <a name="rule-description"></a>規則の説明
 静的メンバーの呼び出しに型のインスタンスは必要ないため、コンストラクターは不要です。 また、型が非静的メンバーを持たないためインスタンスを作成するは提供されませんアクセスを型のメンバーのいずれか。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、既定のコンス トラクターを削除するか、プライベートになります。

> [!NOTE]
>  型では、コンス トラクターが定義されていない場合、一部のコンパイラは自動的にパブリックの既定のコンス トラクターを作成します。 これは、型の場合とである場合は、違反を防ぐためにプライベートの既定のコンス トラクターを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 コンス トラクターが存在する、型が静的な型ではないことを提案します。

## <a name="example"></a>例
 次の例は、この規則に違反する型を示しています。 ソース コードで既定のコンス トラクターがないことに注意してください。 このコードがアセンブリにコンパイルされると、c# コンパイラは既定コンス トラクターは、この規則に違反するを挿入します。 これを修正するには、プライベート コンス トラクターを宣言します。

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]