---
title: "Ca 1011: 基本型をパラメーターとして渡すことを検討してください |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b8107edf5206e86c270c1e7e66d5cd39ea0da145
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: 基本型をパラメーターとして渡すことを考慮します
|||  
|-|-|  
|TypeName|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 メソッド宣言には、派生型である仮パラメーターが含まれ、メソッドを呼び出して、パラメーターの基本型のメンバーだけです。  
  
## <a name="rule-description"></a>規則の説明  
 メソッドの宣言で基本型をパラメーターとして指定すると、その基本型から派生した型は、メソッドに対応する引数として渡すことができます。 メソッドの本体内の引数を使用する場合に実行される特定のメソッドは、引数の型によって異なります。 派生型によって提供される追加機能が不要で、基本型を使用するメソッドのより広範囲に利用が許可されます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、その基本型にパラメーターの型を変更します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を抑制しても安全です。  
  
-   メソッドは、派生型によって提供される特定の機能が必要な場合  
  
     \- または  
  
-   派生型のみ、またはより強い派生型を適用するのには、メソッドに渡されます。  
  
 このような場合は、コードするより堅牢なため、コンパイラとランタイムによって提供される厳密な型チェックします。  
  
## <a name="example"></a>例  
 次の例では、メソッド、`ManipulateFileStream`でのみ使用できる、<xref:System.IO.FileStream>オブジェクトで、この規則に違反します。 2 番目のメソッド`ManipulateAnyStream`、置き換えることで、ルールを満たす、<xref:System.IO.FileStream>パラメーターを使用して、<xref:System.IO.Stream>です。  
  
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1059: メンバーは特定の具象型を公開できません](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)