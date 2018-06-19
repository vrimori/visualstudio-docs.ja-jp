---
title: Intl.NumberFormat オブジェクト (JavaScript) |Microsoft ドキュメント
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
- NumberFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dcb02dbe0d7a7eef88750c440a4fbcdde3ea7ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640132"
---
# <a name="intlnumberformat-object-javascript"></a>Intl.NumberFormat オブジェクト (JavaScript)
ロケール固有の数値の書式設定を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>パラメーター  
 `numberFormatObj`  
 必須です。 `NumberFormat` オブジェクトを代入する変数名を指定します。  
  
 `locales`  
 省略可能です。 1 つ以上の言語またはロケールのタグを含むロケール文字列の配列。 複数のロケール文字列を含めると、最初のエントリが優先ロケールになるように、優先度の高いものから順に一覧表示されます。 このパラメーターを省略すると、JavaScript ランタイムの既定のロケールが使用されます。 詳細については、次の「解説」を参照してください。  
  
 `options`  
 省略可能です。 数値書式設定オプションを指定する 1 つ以上のプロパティを含むオブジェクト。 詳細については、「解説」を参照してください。  
  
## <a name="remarks"></a>コメント  
 `locales`に従う必要がありますパラメーター [BCP 47](http://tools.ietf.org/html/rfc5646) "EN-US"と"ZH-CN"などの言語またはロケールのタグ。 タグには、言語、地域、国、バリエーションを含めることができます。 言語のタグの例については、次を参照してください。[付録 A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP 47。 `NumberFormat`、追加することも、 **-u** -nu 番号付けシステム拡張機能を指定するサブタグの後に。  
  
 "*言語*-*地域*-u-連 -*numberingsystem*"  
  
 ここで*numberingsystem*次のいずれかの可能性があります: アラブ、arabext、バリ、beng、deva、fullwide、gujr、専門家、hanidec、khmr、knda、laoo、latn、limb、mylm、mong、mymr、orya、tamldec、telu、タイ語、tibt です。  
  
 `options` パラメーターには、次のプロパティを含めることができます。  
  
|プロパティ|説明|使用可能な値 |既定値|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|使用するロケール照合アルゴリズムを指定します。|"lookup" および "best fit"|"best fit"|  
|`style`|数値書式スタイルを指定します。|"decimal"、"percent"、および "currency"|"decimal"|  
|`currency`|ISO 4217 通貨値を英字コードで指定します。 `style` が "currency" に設定されている場合は、この値が必要です。|ISO を参照してください[コード リストの通貨と資金](http://www.currency-iso.org/en/home/tables/table-a1.html)です。|未定義|  
|`currencyDisplay`|通貨を ISO 4217 の英字の通貨コードで表示するか、ローカライズされた通貨記号で表示するか、ローカライズされた通貨名で表示するかを指定します。 この値は、`style` が "currency" に設定されている場合にのみ使用されます。|"code"、"symbol"、および "name"|"symbol"|  
|`useGrouping`|桁区切り記号を使用するかどうかを指定します。|true、false|`true`。|  
|`minimumIntegerDigits`|使用する整数部の最小桁数を指定します。|1 ~ 21 です。|21|  
|`minimumFractionDigits`|。 使用する小数部の最小桁数を指定します。|0 ~ 20 です。|0|  
|`maximumFractionDigits`|使用する小数部の最大桁数を指定します。|この値の範囲は `minimumFractionDigits` ～ 20 です。|20.|  
|`minimumSignificantDigits`|表示する小数部の最小桁数を指定します。|この値の範囲は 1 ～ 21 です。|1|  
|`maximumSignificantDigits`|表示する小数部の最大桁数を指定します。|この値の範囲は`minimumSignificantDigits`に 21 にします。|21|  
  
## <a name="properties"></a>プロパティ  
 `NumberFormat` オブジェクトのプロパティを次の表に示します。  
  
|||  
|-|-|  
|プロパティ|説明|  
|[コンス トラクター](../../javascript/reference/constructor-property-intl-numberformat.md)|数値フォーマッタ オブジェクトを作成する関数を指定します。|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|数値フォーマッタの設定を使用して数値の書式を設定する関数を返します。|  
|[プロトタイプ](../../javascript/reference/prototype-property-intl-numberformat.md)|数値フォーマッタのプロトタイプへの参照を返します。|  
  
## <a name="methods"></a>メソッド  
 `NumberFormat` オブジェクトのメソッドを次の表に示します。  
  
|||  
|-|-|  
|メソッド|説明|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|数値フォーマッタ オブジェクトのプロパティと値を含むオブジェクトを返します。|  
  
## <a name="example"></a>例  
 次の例では、書式オプションを指定して en-US ロケールの `NumberFormat` オブジェクトを作成します。  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## <a name="example"></a>例  
 次の例は、いくつかの異なるロケールとオプションを使用した結果を示しています。  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [toLocaleString (数)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator オブジェクト](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat オブジェクト](../../javascript/reference/intl-datetimeformat-object-javascript.md)