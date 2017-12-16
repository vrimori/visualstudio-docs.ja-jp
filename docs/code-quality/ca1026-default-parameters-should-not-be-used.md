---
title: "Ca 1026: 既定のパラメーターは使わないでください |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0c8a6176d25f8eb8f2e7aa66dc0a00f0490f0910
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: 既定のパラメーターを使用できません
|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|CheckId|CA1026|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 外部から参照できる型には、既定のパラメーターを使用する外部から参照できるメソッドが含まれています。  
  
## <a name="rule-description"></a>規則の説明  
 既定のパラメーターを使用するメソッドでは、下にある、共通言語仕様 (CLS); を許可します。ただし、CLS では、これらのパラメーターに割り当てられている値を無視するコンパイラが使用できます。 既定のパラメーター値を無視するコンパイラ用に記述されたコードでは、既定の各パラメーターの引数を明示的に指定する必要があります。 プログラミング言語間で使用する動作を維持するために、既定のパラメーターを提供するメソッド オーバー ロードを持つ既定のパラメーターを使用するメソッドを置き換えてください。  
  
 コンパイラは、マネージ コードにアクセスするときの既定のパラメーターの値を管理拡張機能の C++ の無視します。 Visual Basic コンパイラを使用する既定のパラメーターを持つメソッドをサポートしている、[オプション](/dotnet/visual-basic/language-reference/modifiers/optional)キーワード。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、既定のパラメーターを指定するメソッド オーバー ロードを持つ既定のパラメーターを使用するメソッドを置き換えます。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、既定のパラメーターを使用するメソッドと同等の機能を提供するオーバー ロードされたメソッドを示します。  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1025: 反復する引数を params 配列で置き換えます](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## <a name="see-also"></a>関連項目  
 [言語への非依存性、および言語非依存コンポーネント](/dotnet/standard/language-independence-and-language-independent-components)