---
title: 日付と時刻文字列 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba0798c5-3574-4434-89f4-3d90be276001
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6218ba273b26243382d1e825b6da961d604917ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569642"
---
# <a name="date-and-time-strings-javascript"></a>日付と時刻文字列 (JavaScript)
JavaScript の日付と時刻文字列を指定し、書式設定するには、いくつかの方法があります。  
  
## <a name="formatting-dates-using-intldatetimeformat"></a>Intl.DateTimeFormat の使用による日付の書式設定  
 Internet Explorer 11 では、[Intl.DateTimeFormat Object](../javascript/reference/intl-datetimeformat-object-javascript.md) がサポートされるようになりました。これは、[ECMAScript 国際化 API 仕様](http://www.ecma-international.org/ecma-402/1.0/)の一部です。 日付の書式を設定するには、このオブジェクトを直接使うか、[toLocaleDateString メソッド (Date)](../javascript/reference/tolocaledatestring-method-date-javascript.md) および [toLocaleTimeString メソッド (Date)](../javascript/reference/tolocaletimestring-method-date-javascript.md) の更新された実装を使うことができます。 [Date オブジェクト](../javascript/reference/date-object-javascript.md)のこれらのメソッドでは、ロケールおよびその他の書式設定オプション用の新しい省略可能なパラメーターをサポートするために、内部的に `Intl.DateTimeFormat` が使われています。  
  
 次の例は、`toLocaleDateString` および `toLocaleTimeString` を使用し、日付と時刻の書式を設定する方法を示しています。 これらのメソッドに渡される最初のパラメーターは、"en-us" などのロケール値です。 2 番目のパラメーターは (存在する場合)、曜日の長い形式などの書式指定オプションを指定します。  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = {  
    weekday: "long", year: "numeric", month: "short",  
    day: "numeric", hour: "2-digit", minute: "2-digit"  
};  
  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleTimeString("en-us", options));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleTimeString("ja-JP", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013  
// ‎Friday‎, ‎Feb‎ ‎1‎, ‎2013‎ ‎06‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎  
// ‎2013‎年‎2‎月‎1‎日 ‎金曜日‎ ‎06‎:‎00  
```  
  
 書式設定オプションの完全な一覧については、「[Intl.DateTimeFormat オブジェクト](../javascript/reference/intl-datetimeformat-object-javascript.md)」をご覧ください。  
  
## <a name="formatting-dates"></a>日付の書式設定  
 Internet Explorer 11 より前では、特に日付と時刻の書式を設定するためのメソッドが JavaScript にありませんでした。 以前のバージョンのブラウザーに独自の日付形式を提供するには、[getDay メソッド (Date)](../javascript/reference/getday-method-date-javascript.md)、[getDate メソッド (Date)](../javascript/reference/getdate-method-date-javascript.md)、[getMonth メソッド (Date)](../javascript/reference/getmonth-method-date-javascript.md)、および [getFullYear メソッド (Date)](../javascript/reference/getfullyear-method-date-javascript.md) を使います  ([getYear メソッド (Date)](../javascript/reference/getyear-method-date-javascript.md) は互換性のために残されているので、使わないでください)。  
  
```JavaScript  
var myDate = new Date("February 3, 2001");  
var myDate = new Date("February 3 2001");  
document.write((myDate.getMonth() + 1) + "-" + myDate.getDate() + "-" + myDate.getFullYear());  
document.write("<br/>");  
document.write((myDate.getMonth() + 1) + "/" + myDate.getDate() + "/" + myDate.getFullYear());  
  
//Output:  
// 2-3-2001  
// 2/3/2001  
```  
  
 独自の時刻書式を指定するには、[getHours メソッド (Date)](../javascript/reference/gethours-method-date-javascript.md)、[getMinutes メソッド (Date)](../javascript/reference/getminutes-method-date-javascript.md)、[getSeconds メソッド (Date)](../javascript/reference/getseconds-method-date-javascript.md)、[getMilliseconds メソッド (Date)](../javascript/reference/getmilliseconds-method-date-javascript.md) を使います。  
  
```JavaScript  
myDate = new Date();  
myDate.setHours(10, 30, 53, 400);  
  
document.write(myDate.getHours() + ":" + myDate.getMinutes() + ":" + myDate.getSeconds() +   
":" + myDate.getMilliseconds());  
  
// Output:   
// 10:30:53:400  
```  
  
## <a name="converting-strings-to-dates"></a>文字列から日付へ変換する  
 `Date` または `Date(dateStr)` を使用して、`Date.parse(dateStr)` オブジェクトを構築する文字列を指定できます。 JavaScript は、次の規則を使用して日付文字列を解析します。  
  
-   最初に [ISO 日付形式](#ISO)を使って、日付文字列の解析を試みます。  
  
    > [!NOTE]
    >  JavaScript では、ISO 8601 拡張形式の簡略化バージョンが使用されます。  
  
-   日付文字列が ISO 形式でなかった場合、JavaScript は[その他の日付形式](#OtherDateFormats)を使って日付を解析しようとします。  
  
<a name="ISO"></a>   
## <a name="iso-date-format"></a>ISO 日付形式  
 ISO 形式は、ISO 8601 拡張形式の簡略化バージョンです。 形式は次のとおりです。  
  
 `YYYY-MM-DDTHH:mm:ss.sssZ`  
  
> [!IMPORTANT]
>  ISO 日付形式は、Internet Explorer 8 標準モードと Quirks モードではサポートされていません。  
  
 この形式の各部の説明を次の表に示します。  
  
|シンボル|説明|値|  
|------------|-----------------|------------|  
|`-`, `:`, `.`, `T`|文字列内の実際の文字。 `T` は、時刻の開始を指定します。||  
|`YYYY`|年。 4 桁の年の代わりに拡張年を使用できます。 詳しくは、このトピックの後半で説明する「[拡張年](../javascript/date-and-time-strings-javascript.md#bkmk_extend)」をご覧ください。||  
|`MM`|月|01 ～ 12|  
|`DD`|月の日付|01 ～ 31|  
|`HH`|時間|00 ～ 24|  
|`mm`|分|00 ～ 59|  
|`ss`|秒。 時刻が指定されている場合、秒とミリ秒は省略可能です。|00 ～ 59|  
|`sss`|Milliseconds|00 ～ 999|  
|`Z`|この位置の値は、次のいずれかの形式になります。 値を省略すると UTC 時刻が使用されます。<br /><br /> -   `Z` は UTC 時刻を表します。<br />-   `+hh:mm` は、入力された時刻が UTC 時刻より後の指定されたオフセットであることを示します。<br />-   `-hh:mm` は、入力された時刻が UTC 時刻より前の絶対値であることを示します。||  
  
 文字列には、`YYYY`、`YYYY-MM`、`YYYY-MM-DD` の形式で日付のみを含めることもできます。  
  
 ISO 形式は、タイム ゾーン名をサポートしていません。 `Z` 位置を使用すると、UTC 時刻からのオフセットを指定できます。 `Z` 位置に値を指定しない場合は、UTC 時刻が使用されます。  
  
 深夜は 00:00 または前日の 24:00 を使用して指定できます。 2010-05-25T00: 00 と 2010-05-24T24: 00 の 2 つの文字列は、同じ時刻を表します。  
  
 ISO 形式で日付を返すには、[toISOString メソッド (Date)](../javascript/reference/toisostring-method-date-javascript.md) を使うことができます。  
  
<a name="bkmk_extend"></a>   
### <a name="extended-years"></a>拡張年  
 "*拡張年*" は 4 桁の代わりに 6 桁を使い、正符号または負符号のプレフィックスが付けられます。 拡張年の例は `+002010` で、`2010` に対応します。 拡張年は、0 年以前または 9999 年以後を表すために使用できます。  
  
 6 桁の形式を使用する場合、正符号または負符号は必ず必要です。 4 桁の形式を使用する場合、符号は記述しないでください。 したがって、`0000` と `+000000` は使用できますが、`000000` と `-0001` はエラーが発生します。 拡張年の 0 は正と見なされるので、正符号のプレフィックスが付けられます。  
  
 [toISOString メソッド (Date)](../javascript/reference/toisostring-method-date-javascript.md) は、0 年以前と 9999 年以後の年に必ず拡張年形式を使います。  
  
> [!NOTE]
>  [!INCLUDE[jsv9](../javascript/includes/jsv9-md.md)]  
  
<a name="OtherDateFormats"></a>   
## <a name="other-date-formats"></a>その他の日付形式  
 日付文字列が ISO 形式でない場合、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は次の規則を使用して値を解析します。  
  
 短い日付  
  
-   この形式では、"06/08/2010" のように、月/日/年の順に記述する必要があります。  
  
-   区切り記号としては、"/" または "-" を使用できます。  
  
 長い日付  
  
-   年、月、および日は、任意の順序で並べることができます。 "June 8 2010" と "2010 June 8" は、どちらも有効です。  
  
-   年は 2 桁または 4 桁を指定できます。 年を 2 桁のみにする場合は、70 以上にする必要があります。  
  
-   月と曜日の名前は 2 文字以上にする必要があります。 2 文字で指定した名前に複数の月または曜日が該当する場合は、最後に一致した名前が使用されます。 たとえば、"Ju" は 6 月ではなく 7 月になります。  
  
-   指定した曜日が指定した残りの日付に合わない場合、曜日は無視されます。 たとえば、"Tuesday November 9 1996" は金曜日であるため "Friday November 9 1996" になります。  
  
 時刻  
  
-   時、分、および秒は、コロンで区切ります。 ただし、一部を省略することもできます。 "10:"、"10:11"、および "10:11:12" はいずれも有効です。  
  
-   PM を付加して 13 以上の時間を指定すると NaN が返されます。 たとえば、"23:15 PM" を指定すると NaN が返されます。  
  
 全般  
  
-   無効な日付を含む文字列を指定すると NaN が返されます。 たとえば、2 つの年または 2 つの月を指定すると NaN が返されます。  
  
-   [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は、すべての標準時間帯、世界協定時刻 (UTC)、およびグリニッジ標準時 (GMT) をサポートします。 ISO 形式は、タイム ゾーンをサポートしていません。  
  
-   かっこで囲まれた文字列はコメントとして扱われます。 かっこは入れ子にできます。  
  
-   コンマとスペースは区切り記号として扱われます。 複数の区切り記号を使用できます。  
  
## <a name="example"></a>例  
 次のコードは、それぞれ異なる日付と時刻の文字列の解析結果を表示します。  
  
```  
document.writeln((new Date("2010")).toUTCString());   
  
document.writeln((new Date("2010-06")).toUTCString());  
  
document.writeln((new Date("2010-06-09")).toUTCString());  
  
 // Specifies Z, which indicates UTC time.  
document.writeln((new Date("2010-06-09T15:20:00Z")).toUTCString());  
  
 // Specifies -07:00 offset, which is equivalent to Pacific Daylight time.  
document.writeln((new Date("2010-06-09T15:20:00-07:00")).toGMTString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("June 9, 2010")).toUTCString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("2010 June 9")).toUTCString());  
  
// Specifies a non-ISO Short date and time.  
document.writeln((new Date("6/9/2010 3:20 pm")).toUTCString());  
  
// Output:  
// Fri, 1 Jan 2010 00:00:00 UTC  
// Tue, 1 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 15:20:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
```  
  
 ローカル タイムが指定されている場合の結果は、タイム ゾーンによって異なります。  
  
> [!IMPORTANT]
>  ISO 日付形式は、Internet Explorer 8 標準モードと Quirks モードではサポートされていません。  
  
## <a name="see-also"></a>関連項目  
 [Date オブジェクト](../javascript/reference/date-object-javascript.md)   
 [Date.parse 関数](../javascript/reference/date-parse-function-javascript.md)