---
title: "日付のオブジェクト (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Date
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, determining
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb5d53f3bddfeb3a3ed1ab36e2b4be822964eba5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-javascript"></a>Date オブジェクト (JavaScript)
日付および時刻を格納しておくオブジェクトです。必要に応じて、データの必要な部分を取り出すことができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 `Date` オブジェクトを代入する変数名を指定します。  
  
 `dateVal`  
 必須です。 数値で指定する場合、`dateVal` は、指定した日付と 1970 年 1 月 1 日午前 00:00:00 との間を、ミリ秒単位の数値を使って世界協定時刻で表します。 場合、文字列`dateVal`の規則に従って解析される[日付と時刻文字列](../../javascript/date-and-time-strings-javascript.md)です。 `dateVal` 引数は、一部の ActiveX オブジェクトから返される VT_DATE 値にすることもできます。  
  
 `year`  
 必須です。 4 桁の年 (76 ではなく 1976 など) を指定します。  
  
 `month`  
 必須です。 月を表す 0 ～ 11 (1 ～ 12 月に相当) の範囲内の整数を指定します。  
  
 `date`  
 必須です。 日を表す 1 ～ 31 の範囲内の整数を指定します。  
  
 `hours`  
 省略可能です。 引数 `minutes` を指定する場合は、この引数を指定する必要があります。 時を表す 0 ～ 23 (午前 0 時 ～ 午後 11 時に対応) の範囲内の整数を指定します。  
  
 分  
 省略可能です。 引数 `seconds` を指定する場合は、この引数を指定する必要があります。 分を表す 0 ～ 59 の範囲内の整数を指定します。  
  
 `seconds`  
 省略可能です。 引数 `milliseconds` を指定する場合は、この引数を指定する必要があります。 秒を表す 0 ～ 59 の範囲内の整数を指定します。  
  
 `ms`  
 省略可能です。 ミリ秒を表す 0 ～ 999 の範囲内の整数を指定します。  
  
## <a name="remarks"></a>コメント  
 `Date` オブジェクトには、特定の時刻をミリ秒で表す数値が格納されます。 引数に有効範囲を超える値や負の値を指定すると、値に応じて格納される他の値が変更されます。 たとえば、150 秒を指定すると、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で 2 分 30 秒として処理されます。  
  
 格納されている数値が `NaN` の場合は、オブジェクトが特定の時刻を表していないことを示します。 `Date` オブジェクトに渡すパラメーターがない場合は、現在の時刻 (UTC) で初期化されます。 値は、オブジェクトを使用する前に指定する必要があります。  
  
 `Date` オブジェクトで表せる日付の範囲は、1970 年 1 月 1 日の前後の約 285,616 年です。  
  
 参照してください[を計算する日付と時刻 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)の使用方法に関する詳細について、`Date`オブジェクトおよび関連するメソッド。  
  
## <a name="example"></a>例  
 次のコードは、`Date` オブジェクトの使用例です。  
  
```JavaScript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## <a name="requirements"></a>要件  
 `Date object` は、[!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] で導入されました。 次の一覧にあるメンバーの一部は、それ以降のバージョンで導入されています。 詳細については、次を参照してください。[バージョン情報](../../javascript/reference/javascript-version-information.md)または個々 のメンバーに関するドキュメントです。  
  
## <a name="properties"></a>プロパティ  
 `Date Object` のプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[constructor プロパティ](../../javascript/reference/constructor-property-date.md)|オブジェクトを作成する関数を指定します。|  
|[prototype プロパティ](../../javascript/reference/prototype-property-date.md)|指定されたオブジェクトのクラスのプロトタイプへの参照を返します。|  
  
## <a name="functions"></a>関数  
 `Date Object` の関数を次の表に示します。  
  
|関数|説明|  
|---------------|-----------------|  
|[Date.now 関数](../../javascript/reference/date-now-function-javascript.md)|1970 年 1 月 1 日と現在の日付と時刻の間をミリ秒単位で返します。|  
|[Date.parse 関数](../../javascript/reference/date-parse-function-javascript.md)|日付を表す文字列を解析し、その日付と 1970 年 1 月 1 日午前 00:00:00 との差を表すミリ秒単位の値を返します。|  
|[Date.UTC 関数](../../javascript/reference/date-utc-function-javascript.md)|世界協定時刻 (UTC) (つまり GMT) の 1970 年 1 月 1 日 0 時 0 分 0 秒と、指定した日付との間をミリ秒単位で返します。|  
  
<a name="js56jsobjdatemeth"></a>   
## <a name="methods"></a>メソッド  
 `Date Object` のメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[getDate メソッド](../../javascript/reference/getdate-method-date-javascript.md)|日付の値を現地時刻で返します。|  
|[getDay メソッド](../../javascript/reference/getday-method-date-javascript.md)|曜日の値を現地時刻で返します。|  
|[getFullYear メソッド](../../javascript/reference/getfullyear-method-date-javascript.md)|年の値を現地時刻で返します。|  
|[getHours メソッド](../../javascript/reference/gethours-method-date-javascript.md)|時 (時間) の値を現地時刻で返します。|  
|[getMilliseconds メソッド](../../javascript/reference/getmilliseconds-method-date-javascript.md)|ミリ秒の値を現地時刻で返します。|  
|[getMinutes メソッド](../../javascript/reference/getminutes-method-date-javascript.md)|分の値を現地時刻で返します。|  
|[getMonth メソッド](../../javascript/reference/getmonth-method-date-javascript.md)|月の値を現地時刻で返します。|  
|[getSeconds メソッド](../../javascript/reference/getseconds-method-date-javascript.md)|秒の値を現地時刻で返します。|  
|[getTime メソッド](../../javascript/reference/gettime-method-date-javascript.md)|`Date` オブジェクトに格納されている時刻値を、1970 年 1 月 1 日午前 00:00:00 以降のミリ秒として返します。|  
|[getTimezoneOffset メソッド](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|ホスト コンピューターの時刻と世界協定時刻 (UTC) との差を分単位の値で返します。|  
|[getUTCDate メソッド](../../javascript/reference/getutcdate-method-date-javascript.md)|日付の値を UTC で返します。|  
|[getUTCDay メソッド](../../javascript/reference/getutcday-method-date-javascript.md)|曜日の値を UTC で返します。|  
|[getUTCFullYear メソッド](../../javascript/reference/getutcfullyear-method-date-javascript.md)|年の値を UTC で返します。|  
|[getUTCHours メソッド](../../javascript/reference/getutchours-method-date-javascript.md)|時 (時間) の値を UTC で返します。|  
|[getUTCMilliseconds メソッド](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|ミリ秒の値を UTC で返します。|  
|[getUTCMinutes メソッド](../../javascript/reference/getutcminutes-method-date-javascript.md)|分の値を UTC で返します。|  
|[getUTCMonth メソッド](../../javascript/reference/getutcmonth-method-date-javascript.md)|月の値を UTC で返します。|  
|[getUTCSeconds メソッド](../../javascript/reference/getutcseconds-method-date-javascript.md)|秒の値を UTC で返します。|  
|[getVarDate メソッド](../../javascript/reference/getvardate-method-date-javascript.md)|`Date` オブジェクトの VT_DATE 値を返します。|  
|[getYear メソッド](../../javascript/reference/getyear-method-date-javascript.md)|年の値を返します。|  
|[hasOwnProperty メソッド](../../javascript/reference/hasownproperty-method-object-javascript.md)|指定した名前のプロパティがオブジェクトにあるかどうかを表すブール値を返します。|  
|[isPrototypeOf メソッド](../../javascript/reference/isprototypeof-method-object-javascript.md)|オブジェクトが、別のオブジェクトのプロトタイプ チェーンに存在するかどうかを表すブール値を返します。|  
|[propertyIsEnumerable メソッド](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|指定したプロパティがオブジェクトの一部であるかどうか、および列挙可能かどうかを表すブール値を返します。|  
|[setDate メソッド](../../javascript/reference/setdate-method-date-javascript.md)|月の日付の数値を現地時刻で設定します。|  
|[setFullYear メソッド](../../javascript/reference/setfullyear-method-date-javascript.md)|年の値を現地時刻で設定します。|  
|[setHours メソッド](../../javascript/reference/sethours-method-date-javascript.md)|時 (時間) の値を現地時刻で設定します。|  
|[setMilliseconds メソッド](../../javascript/reference/setmilliseconds-method-date-javascript.md)|ミリ秒の値を現地時刻で設定します。|  
|[setMinutes メソッド](../../javascript/reference/setminutes-method-date-javascript.md)|分の値を現地時刻で設定します。|  
|[setMonth メソッド](../../javascript/reference/setmonth-method-date-javascript.md)|月の値を現地時刻で設定します。|  
|[setSeconds メソッド](../../javascript/reference/setseconds-method-date-javascript.md)|秒の値を現地時刻で設定します。|  
|[setTime メソッド](../../javascript/reference/settime-method-date-javascript.md)|`Date` オブジェクトの日付と時刻の値を設定します。|  
|[setUTCDate メソッド](../../javascript/reference/setutcdate-method-date-javascript.md)|月の日付の数値を UTC で設定します。|  
|[setUTCFullYear メソッド](../../javascript/reference/setutcfullyear-method-date-javascript.md)|年の値を UTC で設定します。|  
|[setUTCHours メソッド](../../javascript/reference/setutchours-method-date-javascript.md)|時間 (時) の値を UTC で設定します。|  
|[setUTCMilliseconds メソッド](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|ミリ秒の値を UTC で設定します。|  
|[setUTCMinutes メソッド](../../javascript/reference/setutcminutes-method-date-javascript.md)|分の値を UTC で設定します。|  
|[setUTCMonth メソッド](../../javascript/reference/setutcmonth-method-date-javascript.md)|月の値を UTC で設定します。|  
|[setUTCSeconds メソッド](../../javascript/reference/setutcseconds-method-date-javascript.md)|秒の値を UTC で設定します。|  
|[setYear メソッド](../../javascript/reference/setyear-method-date-javascript.md)|年の値を現地時刻で設定します。|  
|[toDateString メソッド](../../javascript/reference/todatestring-method-date-javascript.md)|日付を文字列値として返します。|  
|[toGMTString メソッド](../../javascript/reference/togmtstring-method-date-javascript.md)|グリニッジ標準時 (GMT) を使用して日付データを文字列に変換します。|  
|[toISOString メソッド](../../javascript/reference/toisostring-method-date-javascript.md)|日付を ISO 形式の文字列値として返します。|  
|[toJSON メソッド](../../javascript/reference/tojson-method-date-javascript.md)|JSON シリアル化の前にオブジェクト型のデータを変換するために使用されます。|  
|[toLocaleDateString メソッド](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|ホスト環境の現在のロケールに対応した日付を文字列値で返します。|  
|[toLocaleString メソッド](../../javascript/reference/tolocalestring-date.md)|現在のロケールを使用して、文字列に変換されたオブジェクトを返します。|  
|[toLocaleTimeString メソッド](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|ホスト環境の現在のロケールに対応した時刻を文字列値で返します。|  
|[toString メソッド](../../javascript/reference/tostring-method-date.md)|オブジェクトの値を表す文字列を返します。|  
|[toTimeString メソッド](../../javascript/reference/totimestring-method-date-javascript.md)|時刻を文字列値として返します。|  
|[toUTCString メソッド](../../javascript/reference/toutcstring-method-date-javascript.md)|UTC を使用して日付データを文字列に変換します。|  
|[valueOf メソッド](../../javascript/reference/valueof-method-date.md)|指定されたオブジェクトのプリミティブ値を返します。|  
  
## <a name="see-also"></a>関連項目  
 [日付と時刻の計算 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [日付と時刻文字列](../../javascript/date-and-time-strings-javascript.md)