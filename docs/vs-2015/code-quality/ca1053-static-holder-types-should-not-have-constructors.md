---
title: 'Ca 1053: スタティック ホルダー型はコンス トラクターがありません |Microsoft Docs'
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
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fb4d397a5262245771ffd54aadc08a29c5cfcee8
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589155"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: スタティック ホルダー型にはコンストラクターを含めません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1053: スタティック ホルダー型には、コンス トラクターはありません。](https://docs.microsoft.com/visualstudio/code-quality/ca1053-static-holder-types-should-not-have-constructors)します。

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型または入れ子になったパブリック型で、静的なメンバーのみが宣言されています。また、パブリックまたはプロテクトの既定のコンストラクターが含まれます。

## <a name="rule-description"></a>規則の説明
 静的メンバーの呼び出しに型のインスタンスは必要ないため、コンストラクターは不要です。 また、型が非静的メンバーを持たないためインスタンスを作成するアクセスことはできません型のメンバーのいずれかに。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、既定のコンス トラクターを削除するか、プライベートになります。

> [!NOTE]
>  型はコンス トラクターを定義していない場合、一部のコンパイラは自動的に既定のパブリック コンス トラクターを作成します。 型の場合は場合、違反を防ぐために既定のプライベート コンス トラクターを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 コンス トラクターのプレゼンスは、型が静的な型ではないことを提案します。

## <a name="example"></a>例
 次の例では、この規則に違反する型を示します。 ソース コードで既定のコンス トラクターがないことに注意してください。 このコードがアセンブリにコンパイルされると、c# コンパイラは既定コンス トラクターは、このルールに違反するを挿入します。 これを修正するには、プライベート コンス トラクターを宣言します。

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]



