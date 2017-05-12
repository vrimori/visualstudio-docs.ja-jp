---
title: "組み込みオブジェクト (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "組み込みオブジェクト [JavaScript]"
  - "組み込みオブジェクト [JavaScript]"
ms.assetid: 6520c634-a7d1-4a05-8c1b-2e79f449d2e4
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 組み込みオブジェクト (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は、組み込みオブジェクトを提供します。  `Array`、`Boolean`、`Date`、`Error`、`Function`、**Global**、**JSON**、**Math**、**Number**、`Object`、`RegExp` と `String` の各オブジェクトです。  組み込みオブジェクトには、関連するメソッド、関数、プロパティ、および定数があります。これらの詳細については、[言語リファレンス](../javascript/reference/javascript-reference.md)を参照してください。  
  
## Array オブジェクト  
 配列の添字は、オブジェクトのプロパティと考えることができ、数値インデックスで参照されます。  配列に追加された名前付きプロパティには数字のインデックスを付けることができないことに注意してください。これらは配列要素とは区別されます。  
  
 新しい配列を作成するには、次の例のように **new** 演算子と **Array\(\)**[コンストラクター](../javascript/reference/constructor-property-object-javascript.md)を使用します。  
  
```javascript  
var theMonths = new Array(12);  
theMonths[0] = "Jan";  
theMonths[1] = "Feb";  
theMonths[2] = "Mar";  
theMonths[3] = "Apr";  
theMonths[4] = "May";  
theMonths[5] = "Jun";  
theMonths[6] = "Jul";  
theMonths[7] = "Aug";  
theMonths[8] = "Sep";  
theMonths[9] = "Oct";  
theMonths[10] = "Nov";  
theMonths[11] = "Dec";  
```  
  
 `Array` キーワードを使用して配列を作成すると、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ではその配列に **length** プロパティが割り当てられます。  数値を指定しない場合、長さは 0 に設定され配列はエントリを含みません。  数値を指定すると、長さはその数値に設定されます。  複数のパラメーターを指定すると、パラメーターは配列のエントリとして使用されます。  また、パラメーターの数が length プロパティに割り当てられます。次に例を示します。これは上記の例と同じ内容です。  
  
```javascript  
var theMonths = new Array("Jan", "Feb", "Mar", "Apr", "May", "Jun",   
"Jul", "Aug", "Sep", "Oct", "Nov", "Dec");  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、`Array` キーワードで作成した配列に要素を追加すると、自動的に **length** の値が変更されます。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の配列のインデックスは、常に 1 ではなく 0 から開始されます。そのため、length プロパティは、常に配列の最大のインデックスより 1 だけ大きい数値になります。  
  
## String オブジェクト  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、文字列 \(および数値\) をオブジェクトのように扱えます。  [string オブジェクト](../javascript/reference/string-object-javascript.md)には、文字列内で使用できる特定の組み込みのメソッドがあります。  [substring メソッド](../javascript/reference/substring-method-string-javascript.md)は組み込みメソッドの 1 つで、文字列の一部を返します。  引数として 2 つの数値を指定します。  
  
```javascript  
var aString = "0123456789";  
  
// This code sets aChunk to "456".  
var aChunk = aString.substring(4, 7);  
  
// This code sets anotherChunk to "456", using  
// the lower value index as the starting index.  
var anotherChunk = aString.substring(7, 4);  
  
// This code sets the firstLetter variable to "J"  
// by using the array in the preceding array creation example.  
firstLetter = theMonths[5].substring(0,1);  
```  
  
 `String` オブジェクトのもう 1 つのプロパティは、**length** プロパティです。  このプロパティには、文字列内の文字数が含まれます \(空の文字列の場合は 0\)。  これは、計算でそのまま使用できる数値です。  
  
```javascript  
var howLong = "Hello World".length  // Sets the howLong variable to 11.  
```  
  
## Math オブジェクト  
 **Math** オブジェクトには、定義済みの多数の定数と関数があります。  定数は特定の数値です。  これらの特定の数値の 1 つに、π \(約 3.14159...\) があります。  これは、次の例に示す定数 **Math.PI** です。  
  
```javascript  
var radius = 5;  
var circleArea = Math.PI * radius * radius;  
```  
  
 **Math** オブジェクトの組み込み関数の 1 つに、指数演算メソッドの `Math.pow` があります。これは、数値を指定した回数だけ乗算します。  次の例では、パイ \(π\) と指数演算の両方を使用して、球の体積を計算します。  
  
```javascript  
var volume = (4/3)*(Math.PI*Math.pow(radius,3));  
```  
  
## Date オブジェクト  
 `Date` オブジェクトは、任意の日付や時間を表したり、現在のシステムの日付を取得したり、日付の差を計算したりするときに使用できます。  このオブジェクトには、すべて定義済みのプロパティとメソッドがあります。  通常、`Date` オブジェクトは、曜日、年月日、および時刻 \(時、分、秒、およびミリ秒\) を提供します。  この情報は、GMT \(グリニッジ標準時\) の 1970 年 1 月 1 日 00:00:00.000 から経過したミリ秒数に基づいています \(本来は世界標準時によって発信されるシグナルを参照して定められる世界協定時刻 \(UTC\) という用語を使用することが望ましいと考えられています\)。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、紀元前 250,000 年くらいから西暦 255,000 年くらいまでの日付を処理できます。  
  
 新しい `Date` オブジェクトを作成するには、次の例のように **new** 演算子を使用します。  
  
```javascript  
var toDay = new Date();    
var thisYear = toDay.getFullYear();  
var thisMonth = theMonths[toDay.getMonth()];  
var thisDay = thisMonth  + " " + toDay.getDate() + ", " + thisYear;  
```  
  
## Number オブジェクト  
 **Math** オブジェクトで使用できる特殊な数値定数 \(`PI` など\) に加えて、**Number** オブジェクトを通じて [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] で使用できる定数が他にも複数あります。  
  
|定数|説明|  
|--------|--------|  
|Number.MAX\_VALUE|正または負の最大の数は、約 1.79E\+308 となります。  値はシステムによって異なります。|  
|Number.MIN\_VALUE|正または負の最小の数は、約 5.00E\-324 となります。  値はシステムによって異なります。|  
|Number.NaN|特殊な非数値 \(非数\) です。|  
|Number.POSITIVE\_INFINITY|表現できる最も大きい正の値 \(Number.MAX\_VALUE\) よりも大きい値は、自動的にこの値に変換されます。infinity と表示されます。|  
|Number.NEGATIVE\_INFINITY|表現できる最も小さい負の値 \(\-Number.MAX\_VALUE\) よりも小さい値は、自動的にこの値に変換されます。\-infinity と表示されます。|  
  
 **Number.NaN** は、"非数" として定義される特殊な定数です。 数値として解析できない文字列を解析しようとした場合は、**Number.NaN** が返されます。  `NaN` は、任意の数値および自身との比較は、等しくない結果になります。  `NaN` の結果を評価するには、**Number.NaN** と比較するのではなく、**isNaN\(\)** 関数を使用します。  
  
## JSON オブジェクト  
 JSON は、JavaScript 言語のオブジェクト リテラル表記のサブセットに基づく軽量のデータ交換形式です。  
  
 JSON オブジェクトは JSON テキスト形式との変換のための 2 つの関数を提供します。  [JSON.stringify](../javascript/reference/json-stringify-function-javascript.md) 関数は、オブジェクトおよび配列を JSON テキストにシリアル化します。  [JSON.parse](../javascript/reference/json-parse-function-javascript.md) の関数は、メモリ内オブジェクトを作成するために JSON のテキストを非シリアル化します。  詳しくは、「[JavaScript と .NET の JavaScript Object Notation \(JSON\) の概要](http://go.microsoft.com/fwlink/?LinkId=124098)」を参照してください。  
  
## 参照  
 [JavaScript オブジェクト](../javascript/reference/javascript-objects.md)