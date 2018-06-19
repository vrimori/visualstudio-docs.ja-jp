---
title: toLocaleString (Date) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6dc7b1f38f7e57d1c10f7197bb73b13b3545380
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641352"
---
# <a name="tolocalestring-date"></a>toLocaleString (Date)
現在のロケールまたは指定されたロケールでの既定の書式を使用して、日付データを文字列に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 変換対象の `Date` オブジェクト。  
  
 `locales`  
 省略可能です。 1 つ以上の言語またはロケールのタグを含むロケール文字列の配列。 複数のロケール文字列を含めると、最初のエントリが優先ロケールになるように、優先度の高いものから順に一覧表示されます。 このパラメーターを省略すると、JavaScript ランタイムの既定のロケールが使用されます。  
  
 `options`  
 省略可能です。 比較オプションを指定する 1 つ以上のプロパティを含むオブジェクト。  
  
## <a name="remarks"></a>コメント  
 Internet Explorer 11 以降では、`toLocaleString` は、`Intl.DateTimeFormat` パラメーターと `locales` パラメーターのサポートを追加する `options` を内部的に使用して、比較を実行します。 これらのパラメーターの詳細については、次を参照してください。 [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)です。  
  
> [!IMPORTANT]
>  `locales` パラメーターと `options` パラメーターは、一部のドキュメント モードとブラウザー バージョンではサポートされていません。 詳細については、「必要条件」を参照してください。  
  
 Internet Explorer 10 標準ドキュメント モード、以前のドキュメント モード、および互換捻出モードで `toLocaleString` を使用すると、次のようになります。  
  
-   現在のロケールの長い既定形式に日付データを変換し、`String` オブジェクトに格納したものが返されます。  
  
-   西暦 1601 から 1999 年の場合、日付はユーザーのコントロール パネルの地域設定に基づいた形式になります。  
  
> [!NOTE]
>  `locales` パラメーターを省略する場合、`toLocaleString` はユーザーに結果を表示する目的だけで使用してください。この関数の結果はコンピューターによって異なるため、スクリプト内で値を計算する目的では使用しないでください。  
  
## <a name="example"></a>例  
 `toLocaleString` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="example"></a>例  
 次の例は、ロケールと比較オプションを指定して `toLocaleString` メソッドを使用する方法を示します。  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` パラメーターと `options` パラメーター:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [toLocaleDateString メソッド (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)