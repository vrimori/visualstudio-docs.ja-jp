---
title: "Ca 1045: 参照渡しで型を渡しません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7542e21963f272dd10180203a52bee9994de2cdc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: 型を参照によって渡しません
|||  
|-|-|  
|TypeName|DoNotPassTypesByReference|  
|CheckId|CA1045|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリック型のパブリックまたはプロテクト メソッドには、`ref`をプリミティブ型、参照型または値の型を受け取るパラメーターが、組み込み型のいずれか。  
  
## <a name="rule-description"></a>規則の説明  
 型の参照渡し (を使用して`out`または`ref`) ポインターを値型と参照型の違いの理解と処理を複数の戻り値を持つメソッドの使用経験が必要です。 また、違い`out`と`ref`パラメーターはあまり理解されていません。  
  
 参照型が"参照"によって渡されると、メソッドは、オブジェクトの別のインスタンスを返す、パラメーターを使用する予定です。 (参照型の参照渡しと呼びます二重ポインター、ポインター、または二重の間接参照へのポインターを使用します。)呼び出し規約は、"値"渡しですが、既定値を使用して、参照型を受け取る既にパラメーターは、オブジェクトへのポインターを受け取ります。 ポインターを指しているオブジェクトではなくは、値によって渡されます。 値渡し、メソッドは、ポインターの参照の新しいインスタンスをポイントを変更できないことを意味型、それが指すオブジェクトの内容を変更することができます。 ほとんどのアプリケーションが十分では、する動作が生成されます。  
  
 メソッドは、別のインスタンスを返す必要があります、これを実現するのに、メソッドの戻り値を使用します。 参照してください、<xref:System.String?displayProperty=fullName>文字列に対して機能し、文字列の新しいインスタンスを返すメソッドのさまざまなクラスです。 このモデルを使用すると、元のオブジェクトが保存されているかどうかを判断する、呼び出し元に任されています。  
  
 戻り値は一般的であり使用頻度の高いの適切なアプリケーションが`out`と`ref`パラメーターは、中間の設計とコーディングのスキルが必要です。 設計には一般的なユーザーではユーザー扱い方を習得することは期待しないでライブラリ アーキテクト`out`または`ref`パラメーター。  
  
> [!NOTE]
>  値渡しする場合は、大きな構造体パラメーターを使用する場合に、これらの構造をコピーするために必要なその他のリソースでパフォーマンスに影響可能性があります。 このような場合は、使用を検討できる`ref`または`out`パラメーター。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 値の型によって引き起こされるこの規則違反を修正するには、その戻り値としてオブジェクトを返すメソッドがあります。 メソッドは、複数の値を返す必要があります、値を保持するオブジェクトの 1 つのインスタンスが返されるまで設計し直します。  
  
 参照型によって引き起こされるこの規則違反を修正するには、する動作が、参照の新しいインスタンスを返すことを確認します。 である場合、メソッドは、これを行うその戻り値を使用する必要があります。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を抑制しても安全です。ただし、この設計では、ユーザビリティの問題を可能性があります。  
  
## <a name="example"></a>例  
 次のライブラリは、ユーザーのフィードバックに応答を生成するクラスの 2 つの実装を示しています。 最初の実装 (`BadRefAndOut`) ライブラリが 3 つの戻り値の管理を強制します。 2 番目の実装では、(`RedesignedRefAndOut`) コンテナー クラスのインスタンスを返すことによって、ユーザー エクスペリエンスを簡略化 (`ReplyData`) 1 つの単位としてデータを管理します。  
  
 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## <a name="example"></a>例  
 次のアプリケーションは、ユーザーのエクスペリエンスを示しています。 再設計されたライブラリへの呼び出し (`UseTheSimplifiedClass`メソッド) より単純ですが、メソッドによって返される情報が簡単に管理されているとします。 2 つのメソッドからの出力と同じです。  
  
 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## <a name="example"></a>例  
 次のライブラリの例を示して 方法`ref`参照型のパラメーターが使用され、この機能を実装する優れた方法を示しています。  
  
 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## <a name="example"></a>例  
 次のアプリケーションは、動作を示すライブラリ内の各メソッドを呼び出します。  
  
 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
 **ポインターの値渡しを変更するには。**  
**12345**  
**12345**  
**ポインターの参照渡しを変更するには。**  
**12345**  
**12345 ABCDE**  
**戻り値を渡し。**  
**12345 ABCDE**   
## <a name="related-rules"></a>関連規則  
 [CA1021: out パラメーターを使用しません](../code-quality/ca1021-avoid-out-parameters.md)