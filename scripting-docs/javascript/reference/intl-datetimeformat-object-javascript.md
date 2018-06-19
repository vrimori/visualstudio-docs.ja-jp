---
title: Intl.DateTimeFormat オブジェクト (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DateTimeFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c50d6d7d939ebe05ce3ff9b434111413803ea40
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641972"
---
# <a name="intldatetimeformat-object-javascript"></a>Intl.DateTimeFormat オブジェクト (JavaScript)
ロケール固有の日付と時刻の書式設定を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dateTimeFormatObj`  
 必須です。 `DateTimeFormat` オブジェクトを代入する変数名を指定します。  
  
 `locales`  
 省略可能です。 1 つ以上の言語またはロケールのタグを含むロケール文字列の配列。 複数のロケール文字列を含めると、最初のエントリが優先ロケールになるように、優先度の高いものから順に一覧表示されます。 このパラメーターを省略すると、JavaScript ランタイムの既定のロケールが使用されます。 詳細については、次の「解説」を参照してください。  
  
 `options`  
 省略可能です。 日時の書式オプションを指定するプロパティを 1 つ以上含むオブジェクトを指定します。 詳細については、「解説」を参照してください。  
  
## <a name="remarks"></a>コメント  
 `locales`に従う必要がありますパラメーター [BCP 47](http://tools.ietf.org/html/rfc5646) "EN-US"と"ZH-CN"などの言語またはロケールのタグ。 タグには、言語、地域、国、バリエーションを含めることができます。 言語のタグの例については、次を参照してください。[付録 A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP 47。 `DateTimeFormat`、追加することも、 **-u**ロケール文字列に次の Unicode 拡張機能の一方または両方を含めるにサブタグ。  
  
-   -番号付けシステム拡張機能を指定する連:*言語*-*地域*-u-連-*numberingsystem*  
  
     ここで*numberingsystem*次のいずれかの可能性があります: アラブ、arabext、バリ、beng、deva、fullwide、gujr、専門家、hanidec、khmr、knda、laoo、latn、limb、mylm、mong、mymr、orya、tamldec、telu、タイ語、tibt です。  
  
-   カレンダーを指定する ca:*言語*-*地域*-u-ca-*カレンダー*  
  
     ここで*カレンダー*次のいずれかの可能性があります: 仏、中国語、gregory、・ イスラム、islamicc、日本語。  
  
 `options` パラメーターには、次のプロパティを含めることができます。  
  
|プロパティ|説明|使用可能な値 |既定値|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|使用するロケール照合アルゴリズムを指定します。|"lookup" および "best fit"|"best fit"|  
|`formatMatcher`|使用する書式照合アルゴリズムを指定します。|"basic"、"best fit"|"best fit"|  
|`hour12`|時刻の形式で 12 時間制を使用するかどうかを指定します。|`true` (12 時間制の場合)、`false` (24 時間制の場合)||  
|`timeZone`|タイム ゾーンを指定します。 少なくとも、"UTC" は常にサポートされます。|"UTC" などのタイム ゾーンの値。|"UTC"|  
|`weekday`|曜日の書式を指定します。|"narrow"、"short"、"long"。|未定義|  
|`era`|年号の書式を指定します。|"narrow"、"short"、"long"|未定義|  
|`year`|年の書式を指定します。|"2-digit"、"numeric"|未定義または "numeric"|  
|`month`|月の書式を指定します。|"2-digit"、"numeric"、"narrow"、"short"、"long"|未定義または "numeric"|  
|`day`|日の書式を指定します。|"2-digit"、"numeric"|未定義または "numeric"|  
|`hour`|時間の書式を指定します。|"2-digit"、"numeric"|未定義|  
|`minute`|分の書式を指定します。|"2-digit"、"numeric"|未定義|  
|`second`|秒の書式を指定します。|"2-digit"、"numeric"|未定義|  
|`timeZoneName`|タイム ゾーンの書式を指定します。 このプロパティは現在サポートされていません。|"short"、"long"。|このプロパティは現在サポートされていません。|  
  
 `weekday`、`era`、`year`、`month`、`day`、`hour`、`minute`、および `second` の既定値は `undefined` です。 これらのプロパティを設定しなかった場合、`year`、`month`、および `day` の書式には "numeric" が使用されます。  
  
 それぞれのロケールで、少なくとも次の書式をサポートする必要があります。  
  
-   曜日、年、月、日、時間、分、秒  
  
-   曜日、年、月、日  
  
-   年、月、日  
  
-   年、月  
  
-   月、日  
  
-   時間、分、秒  
  
-   時間、分  
  
## <a name="properties"></a>プロパティ  
 `DateTimeFormat` オブジェクトのプロパティを次の表に示します。  
  
|||  
|-|-|  
|プロパティ|説明|  
|[コンス トラクター](../../javascript/reference/constructor-property-intl-datetimeformat.md)|日時フォーマッタ オブジェクトを作成する関数を指定します。|  
|[format](../../javascript/reference/format-property-intl-datetimeformat.md)|日時フォーマッタの設定を使用してロケール固有の日付の書式を設定する関数を返します。|  
|[プロトタイプ](../../javascript/reference/prototype-property-intl-datetimeformat.md)|日時フォーマッタのプロトタイプへの参照を返します。|  
  
## <a name="methods"></a>メソッド  
 `DateTimeFormat` オブジェクトのメソッドを次の表に示します。  
  
|||  
|-|-|  
|メソッド|説明|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|日時フォーマッタ オブジェクトのプロパティと値を含むオブジェクトを返します。|  
  
## <a name="example"></a>例  
 さまざまなロケールを使用して `DateTimeFormat` に日付オブジェクトを渡した結果の例を次に示します。  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## <a name="example"></a>例  
 アラビア語 (サウジアラビア) のロケール、イスラム暦のカレンダー、ラテン語の番号付けシステムを使用して現在の曜日を長い形式で指定する `DateTimeFormat` オブジェクトを作成する例を次に示します。  
  
```JavaScript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [toLocaleString (Date)](../../javascript/reference/tolocalestring-date.md)   
 [toLocaleDateString メソッド (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [toLocaleTimeString メソッド (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Intl.Collator オブジェクト](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.NumberFormat オブジェクト](../../javascript/reference/intl-numberformat-object-javascript.md)