---
title: 'Ca 1061: 基本クラスのメソッドを隠ぺいしない |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3119a088c0dfa7a976a12f0c6abb45e409da8d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: 基本クラス メソッドを非表示にしません
|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 派生型、基本メソッドのいずれかと同じ数のパラメーターと同じ名前のメソッドを宣言します。1 つまたは複数のパラメーターは、基本メソッドの対応するパラメーターの基本型です。いて、残りのパラメーターは、基本メソッドに対応するパラメーターと同じ型です。  
  
## <a name="rule-description"></a>規則の説明  
 基本型のメソッドより弱い派生よりも、基本メソッドのパラメーター シグネチャ内の対応する型を型からのみ派生メソッドのパラメーター シグネチャが異なる場合に、派生型で同じ名前のメソッドによって隠ぺいされます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、削除、メソッドの名前を変更またはパラメーター シグネチャを変更して、メソッドが基本メソッドを隠ぺいしないようにします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、規則に違反するメソッドを示します。  
  
 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]