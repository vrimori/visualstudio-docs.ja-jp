---
title: 'Ca 1009: イベント ハンドラーを正しく宣言します |Microsoft Docs'
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
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b227e11f17a7a20ddf68b9a44317d965538bbab6
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589179"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: イベント ハンドラーを正しく宣言します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1009: イベント ハンドラーを正しく宣言](https://docs.microsoft.com/visualstudio/code-quality/ca1009-declare-event-handlers-correctly)します。

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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例は、デリゲートをイベントの処理に適しています。 このイベント ハンドラーを呼び出すことができるメソッドは、デザイン ガイドラインに指定されているシグネチャに準拠します。 `AlarmEventHandler` デリゲートの型名です。 `AlarmEventArgs` イベントのデータの基本クラスから派生した<xref:System.EventArgs>、およびアラーム イベント データの保持されます。

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA2109: 表示するイベント ハンドラーをレビューします](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>関連項目
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: イベントとデリゲート](http://msdn.microsoft.com/en-us/d98fd58b-fa4f-4598-8378-addf4355a115)



