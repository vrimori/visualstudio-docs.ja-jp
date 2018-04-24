---
title: 'CA1047: Sealed 型の保護されたメンバーを宣言しません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f25af4cf9ddd86bd28b5909242ab55f35a467438
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Sealed 型の保護されたメンバーを宣言しません
|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック型は`sealed`(`NotInheritable` Visual basic で) し、保護されたメンバーまたはプロテクトの入れ子になった型を宣言します。 この規則の違反はレポートされません<xref:System.Object.Finalize%2A>メソッドで、このパターンに従う必要があります。

## <a name="rule-description"></a>規則の説明
 型でプロテクト メンバーを宣言するのは、継承する型からメンバーにアクセスまたはオーバーライドできるようにするためです。 定義上には、sealed 型でメソッドを保護されていることを意味を呼び出すことはできません、シールされた型から継承することはできません。

 C# コンパイラでは、このエラーの警告を発行します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、プライベート、メンバーのアクセス レベルを変更または、型を継承できるようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 現在の状態で、型のままメンテナンスの問題が発生することができ、利点は提供されません。

## <a name="example"></a>例
 次の例は、この規則に違反する型を示しています。

 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]