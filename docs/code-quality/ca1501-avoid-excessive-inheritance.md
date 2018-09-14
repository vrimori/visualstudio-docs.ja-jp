---
title: 'CA1501: 継承を使用しすぎないでください'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0627d246fe9f9f72a95cded7daf8d2c94bf20b3a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546967"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: 継承を使用しすぎないでください

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

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 このルールから警告を抑制しても安全です。 ただし、コードは管理が困難にあります。 基本型の可視性、に応じてこの規則の違反を解決する可能性があります作成重大な変更に注意してください。 たとえば、パブリックの基本型を削除すると、重大な変更です。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]