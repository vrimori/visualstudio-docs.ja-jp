---
title: "Ca 1050: 名前空間の型の宣言 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c0aeaaf3531c45668b8804a6285be5df211c2754
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: 名前空間で型を宣言します
|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 名前付きの名前空間のスコープ外部パブリックまたはプロテクト型で定義されています。  
  
## <a name="rule-description"></a>規則の説明  
 名前空間名の競合を回避して、オブジェクト階層内の関連する型を整理する手段として、型が宣言されます。 コードでは参照できないグローバル名前空間にある、名前付きの名前空間の外部型です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、名前空間で型を配置します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を抑制することはありませんが、これを行うアセンブリは他のアセンブリと共に使用しない場合も安全です。  
  
## <a name="example"></a>例  
 次の例では、名前空間の外部正しく宣言された型を持つライブラリと名前空間で宣言されている同じ名前を持つ型を示します。  
  
 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## <a name="example"></a>例  
 次のアプリケーションでは、以前に定義されているライブラリを使用します。 名前空間の外部で宣言されている型を作成するときに注意してください。 名前`Test`名前空間で修飾されていません。 なおへのアクセス、`Test`入力`Goodspace`、名前空間の名前が必要です。  
  
 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]