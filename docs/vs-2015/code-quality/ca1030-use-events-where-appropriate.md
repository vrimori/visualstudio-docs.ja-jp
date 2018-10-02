---
title: 'Ca 1030: 適切な場所にイベントを使用して |Microsoft Docs'
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
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8100aff6c2215d9a5fa031d69fc0ee105e440e3a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592238"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: 適切な場所にイベントを使用します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1030: 適切な場所にイベントを使用して](https://docs.microsoft.com/visualstudio/code-quality/ca1030-use-events-where-appropriate)します。

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

-   起動

-   発生させる

## <a name="rule-description"></a>規則の説明
 この規則では、通常はイベントに使用される名前を持つメソッドを検出します。 イベントがオブザーバーまたは公開/定期受信デザイン パターンに従ってください。1 つのオブジェクトの状態の変更は、その他のオブジェクトに伝達する必要があるときに使用されます。 明確に定義された状態の変更に応答するメソッドの呼び出しの場合、イベント ハンドラーで、メソッドを呼び出します。 メソッドを呼び出すオブジェクトは、メソッドを直接呼び出すのではなく、イベントを発生させる必要があります。

 イベントの一般的な例は、ボタンのクリックしてなどのユーザー アクションを実行するコードのセグメントによって、ユーザー インターフェイス アプリケーションで表示されます。 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]イベント モデルはユーザー インターフェイスに限定されません。 使用する任意の場所が 1 つまたは複数のオブジェクトの変更の状態を通信する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 オブジェクトの状態が変更されたときに、メソッドを呼び出す場合は、使用するデザインを変更するを検討してください、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]イベント モデル。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制するでは、メソッドが機能しない場合、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]イベント モデル。



