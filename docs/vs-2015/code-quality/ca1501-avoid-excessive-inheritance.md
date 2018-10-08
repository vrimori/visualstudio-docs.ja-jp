---
title: 'CA1501: 過剰な継承の回避 |Microsoft Docs'
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
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: febffd0b9e2fb0275cab1a8055515c83fade5a12
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589624"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: 継承を使用しすぎないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1501: 過剰な継承](https://docs.microsoft.com/visualstudio/code-quality/ca1501-avoid-excessive-inheritance)します。

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型が、その継承階層内の 5 つ以上深いレベルにあります。

## <a name="rule-description"></a>規則の説明
 深いレベルで入れ子にされた型の確認、理解、および保守は困難です。 このルールは、同じモジュール内の階層に分析を制限します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、継承階層の深い未満である基本型から型を派生または中間の基本型の一部を排除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールから警告を抑制しても安全です。 ただし、コードは管理が困難にあります。 基本型の可視性、に応じてこの規則の違反を解決する可能性があります作成重大な変更に注意してください。 たとえば、パブリックの基本型を削除すると、重大な変更です。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]



