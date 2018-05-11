---
title: 'CA1030: 適切な場所にイベントを使用します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9349321319b8bab81a2d9e7b52e7f2d25e87f796
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: 適切な場所にイベントを使用します
|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック、プロテクト、またはプライベート メソッドの名前は、次のいずれかで始まります。

-   アドオン

-   RemoveOn

-   Fire

-   発生させる

## <a name="rule-description"></a>規則の説明
 この規則では、通常はイベントに使用される名前を持つメソッドを検出します。 イベント、オブザーバーまたは発行/サブスクライブ デザイン パターンに従います。その他のオブジェクトに 1 つのオブジェクトの状態の変更を伝達する必要があるときに使用します。 明確に定義された状態の変化への応答で、メソッドによって呼び出された場合は、イベント ハンドラーがメソッドを呼び出す必要があります。 メソッドを呼び出すオブジェクトは、メソッドを直接呼び出すのではなく、イベントを発生させる必要があります。

 イベントの一般的な例は、ボタンのクリックしてなど、ユーザーの操作を実行するコードのセグメントによって、ユーザー インターフェイス アプリケーションが見つかりません。 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]イベント モデルはユーザー インターフェイスに限定されません以外の場合は、使用する任意の場所が 1 つまたは複数のオブジェクトの変更の状態を伝える必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 メソッドが呼び出された場合、オブジェクトの状態が変更されたときに、使用する設計の変更を検討する必要があります、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]イベント モデル。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 メソッドが使用できない場合は、この規則による警告を抑制する、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]イベント モデル。