---
title: 'Ca 1053: スタティック ホルダー型にコンス トラクターはありません |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: a0a17b60cd88170a1df2ace72b8a4ee5206fe6d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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