---
title: 'Ca 1047: sealed 型の保護対象のメンバーを宣言しません |Microsoft Docs'
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
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2cb15dc0befc6ede58f6f66788cb9bf8a3629f73
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287873"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Sealed 型の保護されたメンバーを宣言しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック型が`sealed`(`NotInheritable` Visual basic) とプロテクト メンバーまたはプロテクトの入れ子になった型を宣言します。 このルールの違反はレポートされません<xref:System.Object.Finalize%2A>メソッドで、このパターンに従う必要があります。

## <a name="rule-description"></a>規則の説明
 型でプロテクト メンバーを宣言するのは、継承する型からメンバーにアクセスまたはオーバーライドできるようにするためです。 定義上、sealed 型でメソッドを保護されていることを意味を呼び出すことはできません、シールされた型から継承することはできません。

 C# コンパイラでは、このエラーの警告を発行します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するをプライベート メンバーのアクセス レベルを変更または、型が継承できるようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 メンテナンスの問題が発生することができ、すべての特典を提供しない型の現在の状態のままになります。

## <a name="example"></a>例
 次の例では、この規則に違反する型を示します。

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]



