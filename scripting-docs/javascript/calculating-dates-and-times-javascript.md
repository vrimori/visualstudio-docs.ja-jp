---
title: 日付と時刻の計算 (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- date and time arithmetic [JavaScript]
- JavaScript, date and time
- date comparison [JavaScript]
- date and time calculations [JavaScript]
ms.assetid: ea976f78-d934-479b-9056-880390d8bddd
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 18b4ff307c8f2c48a37ed9ca50e7c5f1ff693ece
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569502"
---
# <a name="calculating-dates-and-times-javascript"></a>日付と時刻の計算 (JavaScript)
[Date オブジェクト](../javascript/reference/date-object-javascript.md)を使うと、日付の比較や経過時間の計算など、カレンダーと時計に関する一般的なタスクを実行できます。  
  
## <a name="setting-a-date-to-the-current-date"></a>現在の日付への日付の設定  
 日付を指定せずに [Date オブジェクト](../javascript/reference/date-object-javascript.md)のインスタンスを作成すると、年、月、日、時、分、秒、およびミリ秒を含む現在の日付と時刻を表す値が返されます。 その後、この日時値を読み取りまたは変更できます。  
  
 パラメーターを使わずに日付をインスタンス化して *mm-dd-yy* の形式で表示する方法の例を次に示します。  
  
```JavaScript  
var dt = new Date();  
  
// Display the month, day, and year. getMonth() returns a 0-based number.  
var month = dt.getMonth()+1;  
var day = dt.getDate();  
var year = dt.getFullYear();  
document.write(month + '-' + day + '-' + year);  
  
// Output: current month, day, year  
```  
  
## <a name="setting-a-specific-date"></a>特定の日付の設定  
 コンストラクターに日付文字列を渡すことによって、特定の日付を設定できます。  
  
```JavaScript  
var dt = new Date('8/24/2009');  
document.write(dt);  
  
// Output: Mon Aug 24 00:00:00 PDT 2009  
  
```  
  
> [!IMPORTANT]
>  日付文字列に表示されるタイム ゾーンは、ローカル コンピューターに設定されているタイム ゾーンに対応します。  
>   
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は、パラメーターとして使用する文字列の書式について柔軟性があります。 たとえば、「8-24-2009」、「August 24, 2009」、「24 Aug 2009」を入力できます。  
  
 時刻を指定することもできます。 ISO 形式で日時を指定する方法の例を次に示します。 "Z" は UTC 時刻を表します。  
  
```JavaScript  
var dt = new Date('2010-06-09T15:20:00Z');  
document.write(dt);  
document.write("<br />");  
document.write(dt.toISOString());  
  
// Output:  
// Wed Jun 09 2010 08:20:00 GMT-0700 (Pacific Daylight Time)  
// 2010-06-09T15:20:00.000Z  
```  
  
 ISO などの日付形式について詳しくは、「[日付と時刻文字列](../javascript/date-and-time-strings-javascript.md)」をご覧ください。  
  
 時刻を指定する別の方法の例を次に示します。  
  
```JavaScript  
var dtA = new Date('8/24/2009 14:52:10');  
  
// The parameters are year, month, day, hours, minutes, seconds.  
var dtB = new Date(2009, 7, 24, 14, 52, 10);  
document.write(dtA);  
document.write("<br/>");  
document.write(dtB);  
  
// Output:  
// Mon Aug 24 14:52:10 PDT 2009  
// Mon Aug 24 14:52:10 PDT 2009  
  
```  
  
## <a name="adding-and-subtracting-days-months-and-years"></a>日、月、および年の加算と除算  
 `Date` オブジェクトの getX メソッドと setX メソッドを使用して、特定の日付と時刻を設定できます。  
  
 次の例は、日付を前日の日付に設定する方法を示しています。 必要に応じて、月、および年の値も変更されることに注意してください。  
  
```JavaScript  
var myDate = new Date("1/1/1990");  
var dayOfMonth = myDate.getDate();  
myDate.setDate(dayOfMonth - 1);  
  
document.write(myDate);  
  
// Output: Sun Dec 31 00:00:00 PST 1989  
```  
  
 次の例では、翌月の最初の日から 1 日を減算することで日付を月の最後の日に設定します。  
  
> [!TIP]
>  各月には、0 (1 月) ～ 11 (12 月) の番号が付けられています。 各曜日には、0 (日曜日) ～ 6 (土曜日) の番号が付けられています。  
  
```JavaScript  
var myDate = new Date("1/1/1990")  
myDate.setMonth(myDate.getMonth() + 1);  
  
myDate.setDate (myDate.getDate() - 1);  
  
document.write(myDate);  
  
// Output: Wed Jan 31 00:00:00 PST 1990  
  
```  
  
## <a name="working-with-days-of-the-week"></a>曜日の操作  
 [getDay メソッド](../javascript/reference/getday-method-date-javascript.md)は、0 (日曜日) から 6 (土曜日) の数値として曜日を取得します  (これは、1 から 31 の数値として日付を取得する [getDate メソッド](../javascript/reference/getdate-method-date-javascript.md)とは異なります)。  
  
 11 月の第 4 木曜日として定義されている米国の感謝祭の休日の日付を設定する例を次に示します。 このスクリプトは、現在の年の 11 月 1 日を検索し、最初の木曜日を検索した後で、3 週間を加算します。  
  
```JavaScript  
var myDate = new Date();  
myDate.setHours(0, 0, 0, 0);  
  
myDate.setYear(2013);  
  
// Determine November 1.  
myDate.setDate(1);  
myDate.setMonth(10);  
  
// Find Thursday.  
var thursday = 4;  
while(myDate.getDay() != thursday) {  
    myDate.setDate(myDate.getDate() + 1);  
}  
  
// Add 3 weeks.  
myDate.setDate(myDate.getDate() + 21);  
  
document.write(myDate);  
  
// Output: Thu Nov 28 00:00:00 <time zone> 2013  
  
```  
  
## <a name="calculating-elapsed-time"></a>経過時間の計算  
 [getTime メソッド](../javascript/reference/gettime-method-date-javascript.md)は、1970 年 1 月 1 日午前 00:00:00 から経過したミリ秒数を返します。 それより前の日付に対しては、負数を返します。  
  
 経過時間を計算するために、[getTime メソッド](../javascript/reference/gettime-method-date-javascript.md)を使って開始時間と終了時間を設定できます。 これにより、数秒間のような小さい単位も、数日間のような大きい単位も計測できます。  
  
 次の例では、秒単位の経過時間を計算します。 [getTime メソッド](../javascript/reference/gettime-method-date-javascript.md)は、ゼロ日付からのミリ秒数を取得します。  
  
```JavaScript  
var startTime = new Date('1/1/1990');  
var startMsec = startTime.getMilliseconds();  
startTime.setTime(5000000);  
var elapsed = (startTime.getTime() - startMsec) / 1000;   
document.write(elapsed);  
  
// Output: 5000  
  
```  
  
 より扱いやすい単位にするために、[getTime メソッド](../javascript/reference/gettime-method-date-javascript.md)から返されたミリ秒数を適切な数値で除算できます。 たとえば、ミリ秒数を日数に変換するには、値を 86,400,000 (1000 ミリ秒 x 60 秒 x 60 分 x 24 時間) で除算します。  
  
 次の例では、指定された年の最初の日からの経過時間を表示します。 除算演算を使用して、日、時、分、および秒単位の経過時間を計算します。 夏時間については考慮しません。  
  
```JavaScript  
// Set the unit values in milliseconds.  
var msecPerMinute = 1000 * 60;  
var msecPerHour = msecPerMinute * 60;  
var msecPerDay = msecPerHour * 24;  
  
// Set a date and get the milliseconds  
var date = new Date('6/15/1990');  
var dateMsec = date.getTime();  
  
// Set the date to January 1, at midnight, of the specified year.  
date.setMonth(0);  
date.setDate(1);  
date.setHours(0, 0, 0, 0);  
  
// Get the difference in milliseconds.  
var interval = dateMsec - date.getTime();  
  
// Calculate how many days the interval contains. Subtract that  
// many days from the interval to determine the remainder.  
var days = Math.floor(interval / msecPerDay );  
interval = interval - (days * msecPerDay );  
  
// Calculate the hours, minutes, and seconds.  
var hours = Math.floor(interval / msecPerHour );  
interval = interval - (hours * msecPerHour );  
  
var minutes = Math.floor(interval / msecPerMinute );  
interval = interval - (minutes * msecPerMinute );  
  
var seconds = Math.floor(interval / 1000 );  
  
// Display the result.  
document.write(days + " days, " + hours + " hours, " + minutes + " minutes, " + seconds + " seconds.");  
  
//Output: 164 days, 23 hours, 0 minutes, 0 seconds.  
```  
  
### <a name="determining-the-users-age"></a>ユーザーの年齢の計算  
 次の例では、ユーザーの誕生日を使用してユーザーの年齢を年単位で計算します。 現在の年から誕生年を減算し、現在の年の誕生日がまだ来ていない場合はさらに 1 を減算します。  
  
```JavaScript  
var birthday = new Date("8/1/1985");  
var today = new Date();  
var years = today.getFullYear() - birthday.getFullYear();  
  
// Reset birthday to the current year.  
birthday.setFullYear(today.getFullYear());  
  
// If the user's birthday has not occurred yet this year, subtract 1.  
if (today < birthday)  
{  
    years--;  
}  
document.write("You are " + years + " years old.");  
  
// Output: You are <number of years> years old.  
  
```  
  
## <a name="comparing-dates"></a>日付の比較  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の日付を比較するときに、演算子の両側の日付が同じオブジェクトを参照している場合にだけ `==` 演算子が `true` を返すことを念頭に置く必要があります。 したがって、2 つの別々の `Date` オブジェクトが同じ日付に設定されている場合、`date1 == date2` は `false` を返します。 また、時刻なしで日付だけで設定された `Date` オブジェクトは、その日付の午前 0 時に初期化されます。 したがって、たとえば時間を指定せずに設定された 1 つの `Date` を `Date.now` と比較する場合、最初の `Date` は午前 0 時に設定され、`Date.now` は設定されないことに注意してください。  
  
 次の例では、現在の日付が指定された日付と同じか、それよりも前か、それよりも後かを調べます。 `todayAtMidn` に現在の日付を設定するために、このスクリプトは現在の年、月、および日に対する `Date` オブジェクトを作成します。  
  
```JavaScript  
// Get the current date at midnight.  
var now = new Date();   
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set specificDate to a specified date at midnight.  
var specificDate = new Date("9/21/2009");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() == specificDate.getTime())  
{  
    document.write("Same");  
}  
else  
{  
    document.write("Different");  
}  
  
//Output: Different  
```  
  
 この例を変更して、指定した日付が特定の範囲内に含まれるかどうかを確認することもできます。  
  
```JavaScript  
// Get the current date at midnight.  
var now = new Date();  
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set start/end dates to a specified date (ISO format).  
var startDate = new Date("2009-06-09T15:20:00Z");  
var endDate = new Date("2011-06-09T15:20:00Z");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() > startDate.getTime() &&   
    todayAtMidn.getTime() < endDate.getTime()) {  
    document.write("Specified date is within this range.");  
}  
else {  
    document.write("Specified date is not in this range.");  
}  
  
// Output: Specified date is not in this range.  
```  
  
## <a name="see-also"></a>関連項目  
 [Date オブジェクト](../javascript/reference/date-object-javascript.md)