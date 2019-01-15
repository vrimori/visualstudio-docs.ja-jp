---
title: CA1021:out パラメーターを使用しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 10ee8312a0861e65e0717cc6d9bec3d2530a8c80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911862"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021:out パラメーターを使用しません

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型の public または protected のメソッドには、`out`パラメーター。

## <a name="rule-description"></a>規則の説明
 型の参照渡し (を使用して`out`または`ref`) ポインター、値型と参照型の違いの理解および複数の戻り値を持つメソッドの処理の使用経験が必要です。 また、間の差`out`と`ref`パラメーターはあまり理解されていません。

 "参照渡し"で参照型が渡されると、メソッドは、オブジェクトの別のインスタンスを返す、パラメーターを使用する予定です。 参照型の参照渡しは、二重のポインター、ポインター、または二重の間接参照へのポインターを使用するとも呼ばれます。 既に参照型を受け取るパラメーターは、呼び出し規約では、値""渡しですが、既定値を使用して、オブジェクトへのポインターを受け取ります。 ポイントされるオブジェクトではなく、ポインターは、値で渡されます。 メソッドがポインターの参照型の新しいインスタンスを指すように変更できない値の意味で渡します。 ただし、それが指すオブジェクトの内容を変更できます。 ほとんどのアプリケーションが十分では、目的の動作が得られます。

 メソッドは、別のインスタンスを返す必要がある場合は、これを実現する、メソッドの戻り値を使用します。 参照してください、<xref:System.String?displayProperty=fullName>の文字列を操作し、文字列の新しいインスタンスを返すメソッドをさまざまなクラスです。 このモデルを使用すると、呼び出し元が元のオブジェクトが保存されているかどうかを決定する必要があります。

 戻り値は一般的であり使用頻度の高いの適切なアプリケーションが`out`と`ref`パラメーターは、中間の設計とコーディングのスキルが必要です。 ライブラリのアーキテクトが設計には一般的なユーザーはユーザーがマスターの操作を期待できません`out`または`ref`パラメーター。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この値の型によって引き起こされるルールの違反を修正するには、その戻り値としてオブジェクトを返すメソッドがあります。 メソッドは、複数の値を返す必要があります、値を保持するオブジェクトの 1 つのインスタンスが返されるまで設計し直します。

 参照型によって発生したこの規則違反を修正するには、目的の動作が、参照の新しいインスタンスを返すことを確認します。 場合は、メソッドは、これを行うその戻り値を使用する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 このルールから警告を抑制しても安全です。 ただし、この設計では、ユーザビリティの問題を生じる可能性があります。

## <a name="example"></a>例
 次のライブラリは、ユーザーのフィードバックに応答を生成するクラスの 2 つの実装を示しています。 最初の実装 (`BadRefAndOut`) 3 つの戻り値を管理するライブラリが強制されます。 2 番目の実装 (`RedesignedRefAndOut`) コンテナー クラスのインスタンスを返すことによって、ユーザー エクスペリエンスを簡略化 (`ReplyData`) 1 つの単位としてデータを管理します。

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>例
 次のアプリケーションは、ユーザーのエクスペリエンスを示しています。 再設計されたライブラリへの呼び出し (`UseTheSimplifiedClass`メソッド) はより簡単ですが、メソッドによって返される情報が簡単に管理されています。 2 つのメソッドからの出力は同じです。

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>例
 次のライブラリ例方法`ref`参照型のパラメーターは使用され、この機能を実装する方法の向上を示しています。

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>例
 次のアプリケーションでは、ライブラリでは、動作を示すため、各メソッドを呼び出します。

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

この例を実行すると、次の出力が生成されます。

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="try-pattern-methods"></a>パターンのメソッドを実行してください。

### <a name="description"></a>説明
 <xref:System.Int32.TryParse%2A?displayProperty=fullName>のような**Try <Something>**パターンを実装するメソッドではこの違反を起こさないでください。 次の例は、<xref:System.Int32.TryParse%2A?displayProperty=fullName>メソッドを実装する構造体 (値型)を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>関連するルール
 [CA 1045:型を参照によって渡しません](../code-quality/ca1045-do-not-pass-types-by-reference.md)
