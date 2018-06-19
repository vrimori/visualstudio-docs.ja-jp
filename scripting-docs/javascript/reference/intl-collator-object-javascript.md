---
title: Intl.Collator オブジェクト (JavaScript) |Microsoft ドキュメント
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
- Collator
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9a41507face20285124257be95197ef5ea53ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640002"
---
# <a name="intlcollator-object-javascript"></a>Intl.Collator オブジェクト (JavaScript)
ロケール固有の文字列比較を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### <a name="parameters"></a>パラメーター  
 `collatorObj`  
 必須です。 `Collator` オブジェクトを代入する変数名を指定します。  
  
 `locales`  
 省略可能です。 1 つ以上の言語またはロケールのタグを含むロケール文字列の配列。 複数のロケール文字列を含めると、最初のエントリが優先ロケールになるように、優先度の高いものから順に一覧表示されます。 このパラメーターを省略すると、JavaScript ランタイムの既定のロケールが使用されます。 詳細については、次の「解説」を参照してください。  
  
 `options`  
 省略可能です。 比較オプションを指定する 1 つ以上のプロパティを含むオブジェクト。 詳細については、「解説」を参照してください。  
  
## <a name="remarks"></a>コメント  
 `locales`に従う必要がありますパラメーター [BCP 47](http://tools.ietf.org/html/rfc5646) "EN-US"と"Hans-ZH-CN"などの言語またはロケールのタグ。 タグには、言語、地域、国、バリエーションを含めることができます。 言語の一覧は、次を参照してください。、 [IANA 言語サブタグ レジストリ](http://go.microsoft.com/fwlink/p/?linkid=227303)です。 言語のタグの例については、次を参照してください。[付録 A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP 47。 `Collator` では、ロケール文字列に -u 拡張機能を含めて、次の 1 つ以上の Unicode 拡張機能を指定できます。  
  
-   バリアント型の照合順序 (ロケール固有) を指定する -co:"*言語*-*地域*-u-co -*値*"です。  
  
-   数値比較を指定する -kn:"*言語*-*地域*-u kn-true &#124; false"です。  
  
-   -大文字または小文字の文字を最初に並べ替えするかどうかを指定する kf:"*言語*-*地域*-u kf 上 &#124; 下位 &#124; false") です。 この拡張機能は現在サポートされていません。  
  
 数値比較を指定する -kn 拡張機能をロケール文字列に設定したり、使用、`numeric`プロパティに、`options`パラメーター。 使用する場合、`numeric`プロパティ、-kn の値は適用されません。  
  
 `options` パラメーターには、次のプロパティを含めることができます。  
  
-   `localeMatcher`。 使用するロケール照合アルゴリズムを指定します。 有効な値は、"lookup" および "best fit" です。 既定値は "best fit" です。  
  
-   `usage`。 比較の目的が並べ替えであるか検索であるかを指定します。 有効な値は、"sort" および "search" です。 既定値は "sort" です。  
  
-   `sensitivity`。 Collator の感度を指定します。 有効な値は、"base"、"accent"、"case"、および "variant" です。 既定値は `undefined` です。  
  
-   `ignorePunctuation`。 比較で句読点を無視するかどうかを指定します。 有効な値は、"true" および "false" です。 既定値は `false` です。  
  
-   `numeric`。 数値並べ替えを使用するかどうかを指定します。 有効な値は、"true" および "false" です。 既定値は `false` です。  
  
-   `caseFirst`。 現在サポートされていません。  
  
## <a name="properties"></a>プロパティ  
 `Collator` オブジェクトのプロパティを次の表に示します。  
  
|||  
|-|-|  
|プロパティ|説明|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Collator の並べ替え順序を使用して 2 つの文字列を比較する関数を返します。|  
|[コンス トラクター](../../javascript/reference/constructor-property-intl-collator.md)|Collator を作成する関数を指定します。|  
|[プロトタイプ](../../javascript/reference/prototype-property-intl-collator.md)|Collator のプロトタイプへの参照を返します。|  
  
## <a name="methods"></a>メソッド  
 `Collator` オブジェクトのメソッドを次の表に示します。  
  
|||  
|-|-|  
|メソッド|説明|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Collator のプロパティと値を含むオブジェクトを返します。|  
  
## <a name="example"></a>例  
 次の例では、`Collator` オブジェクトを作成して比較を実行します。  
  
```JavaScript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## <a name="example"></a>例  
 次の例では、`Collator` オブジェクトを使用して配列を並べ替えます。 この例は、ロケール固有の違いを示しています。  
  
```JavaScript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## <a name="example"></a>例  
 次の例では、`Collator` オブジェクトを使用して文字列を検索し、比較オプションを指定します。  
  
```JavaScript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [localeCompare メソッド (String)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat オブジェクト](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.NumberFormat オブジェクト](../../javascript/reference/intl-numberformat-object-javascript.md)