---
title: "Ca 1009: イベント ハンドラーを正しく宣言します |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6191676f94300dfbfafcb8ceb6b0874a8e5b558a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: イベント ハンドラーを正しく宣言します
|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクトのイベントを処理するデリゲートには、正しいシグネチャ、戻り値の型、またはパラメーター名がありません。  
  
## <a name="rule-description"></a>規則の説明  
 イベント ハンドラー メソッドでは 2 つのパラメーターを使用します。 型の 1 つは、 <xref:System.Object?displayProperty=fullName> 'sender' という名前です。 これは、イベントを発生させるオブジェクトです。 2 番目のパラメーターの型は<xref:System.EventArgs?displayProperty=fullName>'e' という名前です。 これは、イベントに関連付けられるデータです。 などの場合は、ファイルを開くたびにこのイベントは、イベント データは通常ファイルの名前を表します。  
  
 イベント ハンドラー メソッドは、値を返さない必要があります。 C# でプログラミング言語、これは戻り値の型により表示は`void`します。 イベント ハンドラーは、複数のオブジェクトで複数のメソッドを呼び出すことができます。 メソッドが許可された場合、値を返す、複数の戻り値は、各イベントの発生し、呼び出された最後のメソッドの値だけはできます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、シグネチャ、戻り値の型、またはデリゲートのパラメーター名を修正します。 詳細については、次の例を参照してください。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例は、デリゲートをイベントの処理に適しています。 このイベント ハンドラーで呼び出すことのできるメソッドは、デザイン ガイドラインに指定されているシグネチャを持つ準拠しています。 `AlarmEventHandler`デリゲートの型名です。 `AlarmEventArgs`イベント データの基本クラスから派生した<xref:System.EventArgs>を保持アラーム イベント データとします。  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## <a name="related-rules"></a>関連規則  
 [CA2109: 表示するイベント ハンドラーをレビューします](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [処理と、イベントを発生させる](/dotnet/standard/events/index)  