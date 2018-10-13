---
title: 'Ca 2214: コンス トラクターのオーバーライド可能なメソッドを呼び出さない |Microsoft Docs'
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
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f1ccd614eb14e47401ebab23e41b53679ac2b082
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240423"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: コンストラクターのオーバーライド可能なメソッドを呼び出しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 封印されていない型のコンス トラクターは、そのクラスで定義されている仮想メソッドを呼び出します。

## <a name="rule-description"></a>規則の説明
 仮想メソッドが呼び出されると、実行時までは、メソッドを実行する実際の型が選択されていません。 コンス トラクターは、仮想メソッドを呼び出し、メソッドを呼び出すインスタンスのコンス トラクターが実行しないことになります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、型のコンス トラクター内からに型の仮想メソッドを呼び出す操作を行います。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 コンス トラクターは、仮想メソッド呼び出しを削除して再設計する必要があります。

## <a name="example"></a>例
 次の例では、この規則違反の効果を示します。 テスト アプリケーションのインスタンスを作成する`DerivedType`、それが原因で、基底クラス (`BadlyConstructedType`) コンス トラクターが実行されます。 `BadlyConstructedType`コンス トラクターが仮想メソッドを正しく呼び出します`DoSomething`します。 出力を`DerivedType.DoSomething()`を実行して、前に`DerivedType`のコンス トラクターを実行します。

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 この例を実行すると、次の出力が生成されます。

 **基本コンス トラクターを呼び出しています。** 
 **DoSomething の派生には、呼び出される初期化でしょうか。いいえ**
**呼び出すコンス トラクターを派生します。**



