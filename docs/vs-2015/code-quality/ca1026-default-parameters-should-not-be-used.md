---
title: 'Ca 1026: 既定のパラメーターを使用する |Microsoft Docs'
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
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2cc9f540c463b2f07bb8effa57690dd05e509de6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287353"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: 既定のパラメーターを使用できません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照の型には、既定のパラメーターを使用する、外部から参照できるメソッドが含まれています。

## <a name="rule-description"></a>規則の説明
 既定のパラメーターを使用するメソッドは下で、共通言語仕様 (CLS); を使用します。ただし、CLS では、これらのパラメーターに割り当てられている値を無視するコンパイラが使用できます。 既定のパラメーター値を無視するコンパイラ用に記述されたコードでは、既定の各パラメーターの引数を明示的に指定する必要があります。 プログラミング言語間で使用する動作を維持するためには、既定のパラメーターを提供するメソッドのオーバー ロードを持つ既定のパラメーターを使用するメソッドを置き換える必要があります。

 コンパイラは、マネージ コードにアクセスするときの既定のパラメーターの値を管理拡張機能の C++ の無視します。 Visual Basic コンパイラを使用する既定のパラメーターを持つメソッドをサポートしている、 [(省略可能)](http://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7)キーワード。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、既定パラメーターを指定するメソッドのオーバー ロードを持つ既定のパラメーターを使用するメソッドを置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、既定のパラメーターを使用するメソッドと同等の機能を提供するオーバー ロードされたメソッドを示します。

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1025: 反復する引数を params 配列で置き換えます](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>関連項目
 [言語への非依存性、および言語非依存コンポーネント](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



