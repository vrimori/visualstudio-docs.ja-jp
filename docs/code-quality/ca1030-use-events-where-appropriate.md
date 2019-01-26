---
title: CA1030:適切な場所にイベントを使用します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89ee195da621ea9d7342302efadf582e21f7e619
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956728"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030:適切な場所にイベントを使用します

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック、プロテクト、またはプライベート メソッドの名前は、次のいずれかで始まります。

- アドオン

- RemoveOn

- 起動

- 発生させる

## <a name="rule-description"></a>規則の説明
 この規則では、通常はイベントに使用される名前を持つメソッドを検出します。 イベントがオブザーバーまたは公開/定期受信デザイン パターンに従ってください。1 つのオブジェクトの状態の変更は、その他のオブジェクトに伝達する必要があるときに使用されます。 明確に定義された状態の変更に応答するメソッドの呼び出しの場合、イベント ハンドラーで、メソッドを呼び出します。 メソッドを呼び出すオブジェクトは、メソッドを直接呼び出すのではなく、イベントを発生させる必要があります。

 イベントの一般的な例は、ボタンのクリックしてなどのユーザー アクションを実行するコードのセグメントによって、ユーザー インターフェイス アプリケーションで表示されます。 .NET Framework のイベント モデルはユーザー インターフェイスに限定されません。必ず使用状態が 1 つまたは複数のオブジェクトに変更を伝達する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 オブジェクトの状態が変更されたときに、メソッドを呼び出すと、.NET Framework イベント モデルを使用してデザインを変更するかを検討してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 メソッドは、.NET Framework イベント モデルでは機能しない場合は、この規則による警告を抑制します。