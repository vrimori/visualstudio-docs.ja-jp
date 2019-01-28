---
title: CA2208:引数の例外を正しくインスタンス化します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8ef4e23f0200f17c0f6d59789538352d9e1676ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980181"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208:引数の例外を正しくインスタンス化します

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

考えられる原因は、次の状況を含めます。

- 派生したか、例外の種類の既定の (パラメーターなしの) コンス トラクターの呼び出し<xref:System.ArgumentException>します。

- 無効な文字列引数を渡すかから派生した例外の種類のパラメーター化されたコンス トラクターに<xref:System.ArgumentException>します。

## <a name="rule-description"></a>規則の説明

既定のコンス トラクターを呼び出す代わりには、によりより意味のある例外メッセージを指定するコンス トラクターのオーバー ロードのいずれかを呼び出します。 例外メッセージは、開発者を対象し、明確に、エラー条件および修正するか、例外を回避する方法を説明する必要があります。

1 つまたは複数の文字列のコンス トラクターのシグネチャ<xref:System.ArgumentException>、その派生型を一貫していない、`message`と`paramName`パラメーター。 これらのコンス トラクターが正しい文字列引数を使用して呼び出されることを確認します。 署名は次のとおりです。

 <xref:System.ArgumentException>(文字列`message`)

 <xref:System.ArgumentException>(文字列`message`、文字列`paramName`)

 <xref:System.ArgumentNullException>(文字列`paramName`)

 <xref:System.ArgumentNullException>(文字列`paramName`、文字列`message`)

 <xref:System.ArgumentOutOfRangeException>(文字列`paramName`)

 <xref:System.ArgumentOutOfRangeException>(文字列`paramName`、文字列`message`)

 <xref:System.DuplicateWaitObjectException>(文字列`parameterName`)

 <xref:System.DuplicateWaitObjectException>(文字列`parameterName`、文字列`message`)

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、メッセージ、パラメーター名、またはその両方を受け取るコンス トラクターを呼び出すし、引数が型の適切なことを確認<xref:System.ArgumentException>が呼び出されます。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 パラメーター化されたコンス トラクターが正しい文字列引数で呼び出された場合にのみ、この規則による警告を抑制するのには安全です。

## <a name="example-1"></a>例 1
 次の例では、ArgumentNullException 型のインスタンスを正しくインスタンス化するコンス トラクターを示します。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example-2"></a>例 2
 次の例では、コンス トラクターの引数の切り替えを上記の違反を修正します。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]