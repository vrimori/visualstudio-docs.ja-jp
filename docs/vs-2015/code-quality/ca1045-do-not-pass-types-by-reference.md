---
title: 'Ca 1045: 参照型を渡しません |Microsoft Docs'
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
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1aa9077a0d27c105cd7008d550a4315ce8daf91a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836568"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: 型を参照によって渡しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型の public または protected のメソッドには、`ref`プリミティブ型、参照型または値型を受け取るパラメーターが、組み込み型のいずれか。

## <a name="rule-description"></a>規則の説明
 型の参照渡し (を使用して`out`または`ref`) ポインター、値型と参照型の違いの理解および処理を複数の戻り値を持つメソッドの使用経験が必要です。 また、間の差`out`と`ref`パラメーターはあまり理解されていません。

 "参照渡し"で参照型が渡されると、メソッドは、オブジェクトの別のインスタンスを返す、パラメーターを使用する予定です。 (参照型の参照渡しもと呼びます二重ポインター、ポインター、または二重の間接参照へのポインターを使用します。)呼び出し規約では、値""渡しですが、既定値を使用してを既に参照型を受け取るパラメーターは、オブジェクトへのポインターを受け取ります。 ポイントされるオブジェクトではなく、ポインターは、値で渡されます。 値渡し、メソッドがポインターの参照の新しいインスタンスを指すように変更できないことを意味、入力が指すオブジェクトの内容を変更することができます。 ほとんどのアプリケーションが十分では、する動作が得られます。

 メソッドは、別のインスタンスを返す必要がある場合は、これを実現する、メソッドの戻り値を使用します。 参照してください、<xref:System.String?displayProperty=fullName>の文字列を操作し、文字列の新しいインスタンスを返すメソッドをさまざまなクラスです。 このモデルを使用するには、元のオブジェクトが保存されているかどうかを判断する、呼び出し元に任されておりです。

 戻り値は一般的であり使用頻度の高いの適切なアプリケーションが`out`と`ref`パラメーターは、中間の設計とコーディングのスキルが必要です。 ライブラリのアーキテクトが設計には一般的なユーザーはユーザーがマスターの操作を期待できません`out`または`ref`パラメーター。

> [!NOTE]
>  大きな構造体のパラメーターを使用するときにこれらの構造をコピーするために必要なその他のリソースにより、パフォーマンスに影響値渡しする場合。 このような場合は、使用を検討できます`ref`または`out`パラメーター。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この値の型によって引き起こされるルールの違反を修正するには、その戻り値としてオブジェクトを返すメソッドがあります。 メソッドは、複数の値を返す必要があります、値を保持するオブジェクトの 1 つのインスタンスが返されるまで設計し直します。

 参照型によって発生したこのルールの違反を修正するには、動作するが、参照の新しいインスタンスを返すことを確認します。 場合は、メソッドは、これを行うその戻り値を使用する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制しても安全です。ただし、この設計では、ユーザビリティの問題を生じる可能性があります。

## <a name="example"></a>例
 次のライブラリは、ユーザーのフィードバックに応答を生成するクラスの 2 つの実装を示しています。 最初の実装 (`BadRefAndOut`) 3 つの戻り値を管理するライブラリが強制されます。 2 番目の実装 (`RedesignedRefAndOut`) コンテナー クラスのインスタンスを返すことによって、ユーザー エクスペリエンスを簡略化 (`ReplyData`) 1 つの単位としてデータを管理します。

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>例
 次のアプリケーションは、ユーザーのエクスペリエンスを示しています。 再設計されたライブラリへの呼び出し (`UseTheSimplifiedClass`メソッド) はより簡単ですが、メソッドによって返される情報が簡単に管理されています。 2 つのメソッドからの出力は同じです。

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>例
 次のライブラリ例方法`ref`参照型のパラメーターを使用し、この機能を実装する方法の向上を示しています。

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>例
 次のアプリケーションでは、ライブラリでは、動作を示すため、各メソッドを呼び出します。

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **値渡し Changing ポインター -:**
**12345**
**12345**
**Changing ポインター、参照によって渡される:** 
 **12345**
**12345 ABCDE**
**戻り値渡しで渡す:**
**12345 ABCDE**
## <a name="related-rules"></a>関連規則
 [CA1021: out パラメーターを使用しません](../code-quality/ca1021-avoid-out-parameters.md)



