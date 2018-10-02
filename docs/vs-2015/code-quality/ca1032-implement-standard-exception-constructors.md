---
title: 'Ca 1032: 標準例外コンス トラクターを実装する |Microsoft Docs'
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
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4d8c2f4439cf63f0bab7294898c96b2acb742e7d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589625"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: 標準例外コンストラクターを実装します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1032: 標準例外コンス トラクターを実装](https://docs.microsoft.com/visualstudio/code-quality/ca1032-implement-standard-exception-constructors)します。

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 型拡張<xref:System.Exception?displayProperty=fullName>し、必要なすべてのコンス トラクターを宣言しません。

## <a name="rule-description"></a>規則の説明
 例外の種類には、次のコンス トラクターを実装する必要があります。

-   パブリック NewException()

-   パブリック NewException(string)

-   パブリック NewException (文字列、例外)

-   保護されたまたはプライベート NewException (SerializationInfo, StreamingContext)

 コンストラクターを完全に宣言していないと、例外を正しく処理するのが困難になります。 シグネチャを持つコンス トラクターなど`NewException(string, Exception)`他の例外によって引き起こされる例外を作成するために使用します。 このコンス トラクターのない作成して、インスタンスの内部の (入れ子になった) 例外を含む独自の例外をスローすることはできません、どのようなマネージ コードは、このような状況で行う必要がありますです。 最初の 3 つの例外のコンス トラクターでは、規則でパブリックです。 4 番目のコンス トラクターが封印されていないクラスで保護されているシール クラスではプライベートです。 詳細については、次を参照してください[ca 2229: シリアル化コンス トラクターの実装。](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、例外に不足しているコンス トラクターを追加し、適切なアクセシビリティであるかどうかを確認します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パブリック コンス トラクターを異なるアクセス レベルを使用して、違反が発生する場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例には、この規則に違反する例外の種類と例外の種類が正しく実装されているが含まれています。

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]



