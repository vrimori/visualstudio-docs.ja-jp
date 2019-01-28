---
title: CA1009:イベント ハンドラーを正しく宣言します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 900eca590a87cc45a2859becd4a6a70c09d57bc7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990915"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009:イベント ハンドラーを正しく宣言します

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクトのイベントを処理するデリゲートの型、またはパラメーター名を返す、正しいシグネチャではありません。

## <a name="rule-description"></a>規則の説明
 イベント ハンドラー メソッドでは 2 つのパラメーターを使用します。 型の 1 つは、 <xref:System.Object?displayProperty=fullName> 'sender' という名前です。 これは、イベントを発生させるオブジェクトです。 型の 2 番目のパラメーターが<xref:System.EventArgs?displayProperty=fullName>'e' という名前です。 これは、イベントに関連付けられるデータです。 たとえば、ファイルが開かれるたびに、イベントが発生する場合、イベント データは通常ファイルの名前を表します。

 イベント ハンドラー メソッドは、値を返さないする必要があります。 C# でプログラミング言語、これは戻り値の型により表示は`void`します。 イベント ハンドラーは、複数のオブジェクトで複数のメソッドを呼び出すことができます。 値を返すメソッドが許可された場合は、複数の戻り値は、各イベントの発生し、呼び出された最後のメソッドの値だけができるようにします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、シグネチャ、戻り値の型、またはデリゲートのパラメーター名を修正します。 詳細については、次の例を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例は、デリゲートをイベントの処理に適しています。 このイベント ハンドラーを呼び出すことができるメソッドは、デザイン ガイドラインに指定されているシグネチャに準拠します。 `AlarmEventHandler` デリゲートの型名です。 `AlarmEventArgs` イベントのデータの基本クラスから派生した<xref:System.EventArgs>、およびアラーム イベント データの保持されます。

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA 2109:表示するイベント ハンドラーをレビューします](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>関連項目

- <xref:System.EventArgs?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
- [処理とイベントの発生](/dotnet/standard/events/index)