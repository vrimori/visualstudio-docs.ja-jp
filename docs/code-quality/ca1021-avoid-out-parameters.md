---
title: 'CA1021: out パラメーターを使用しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f62a88d8b3462d50b92cf2c7bcdf577ff736d19b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900460"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: out パラメーターを使用しません
|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型のパブリックまたはプロテクト メソッドには、`out`パラメーター。

## <a name="rule-description"></a>規則の説明
 型の参照渡し (を使用して`out`または`ref`) ポインターを値型と参照型の違いの理解、および複数の戻り値を持つメソッドの処理の使用経験が必要です。 また、違い`out`と`ref`パラメーターはあまり理解されていません。

 参照型が"参照"によって渡されると、メソッドは、オブジェクトの別のインスタンスを返す、パラメーターを使用する予定です。 参照型の参照渡しは double 型のポインター、ポインター、または二重の間接参照へのポインターを使用する場合とも呼ばれます。 呼び出し規約は、"値"渡しですが、既定値を使用して、既に参照型を受け取るパラメーターは、オブジェクトへのポインターを受け取ります。 ポインターを指しているオブジェクトではなくは、値によって渡されます。 メソッドは、ポインターの参照型の新しいインスタンスをポイントを変更できない値の意味を渡します。 ただし、これが指すオブジェクトの内容を変更することができます。 ほとんどのアプリケーションが十分では、目的の動作が生成されます。

 メソッドは、別のインスタンスを返す必要があります、これを実現するのに、メソッドの戻り値を使用します。 参照してください、<xref:System.String?displayProperty=fullName>文字列に対して機能し、文字列の新しいインスタンスを返すメソッドのさまざまなクラスです。 このモデルを使用すると、呼び出し元が元のオブジェクトが保存されているかどうかを決定する必要があります。

 戻り値は一般的であり使用頻度の高いの適切なアプリケーションが`out`と`ref`パラメーターは、中間の設計とコーディングのスキルが必要です。 設計には一般的なユーザーではユーザー扱い方を習得することは期待しないでライブラリ アーキテクト`out`または`ref`パラメーター。

## <a name="how-to-fix-violations"></a>違反の修正方法
 値の型によって引き起こされるこの規則違反を修正するには、その戻り値としてオブジェクトを返すメソッドがあります。 メソッドは、複数の値を返す必要があります、値を保持するオブジェクトの 1 つのインスタンスが返されるまで設計し直します。

 参照型によって引き起こされるこの規則違反を修正するには、目的の動作が、参照の新しいインスタンスを返すことを確認します。 である場合、メソッドは、これを行うその戻り値を使用する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制しても安全です。 ただし、この設計では、ユーザビリティの問題を可能性があります。

## <a name="example"></a>例
 次のライブラリは、ユーザーのフィードバックに応答を生成するクラスの 2 つの実装を示しています。 最初の実装 (`BadRefAndOut`) ライブラリが 3 つの戻り値の管理を強制します。 2 番目の実装では、(`RedesignedRefAndOut`) コンテナー クラスのインスタンスを返すことによって、ユーザー エクスペリエンスを簡略化 (`ReplyData`) 1 つの単位としてデータを管理します。

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>例
 次のアプリケーションは、ユーザーのエクスペリエンスを示しています。 再設計されたライブラリへの呼び出し (`UseTheSimplifiedClass`メソッド) より単純ですが、メソッドによって返される情報が簡単に管理されているとします。 2 つのメソッドからの出力と同じです。

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>例
 次のライブラリの例を示して 方法`ref`参照型のパラメーターを使用し、この機能を実装する優れた方法を示しています。

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>例
 次のアプリケーションは、動作を示すライブラリ内の各メソッドを呼び出します。

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

 この例を実行すると、次の出力が生成されます。

 **変更するポインターの値で渡されます:**
**12345**
**12345**
**Changing ポインター、参照によって渡されます:** 
 **12345**
**12345 ABCDE**
**戻り値渡し:**
**12345 ABCDE**
## <a name="try-pattern-methods"></a>パターンのメソッドを実行してください。

### <a name="description"></a>説明
 実装するメソッド、**再試行\<もの >** パターンなど<xref:System.Int32.TryParse%2A?displayProperty=fullName>、この違反を発生させません。 次の例は、構造体 (値型) を実装する、<xref:System.Int32.TryParse%2A?displayProperty=fullName>メソッドです。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>関連規則
 [CA1045: 型を参照によって渡しません](../code-quality/ca1045-do-not-pass-types-by-reference.md)