---
title: "JSON.stringify 関数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "stringify メソッド"
ms.assetid: 0fafaf3b-c29b-46dc-b65b-ca223064a1d0
caps.latest.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 40
---
# JSON.stringify 関数 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値を JSON \(JavaScript Object Notation\) 文字列に変換します。  
  
## 構文  
  
```  
  
JSON.stringify(  
value [, replacer] [, space])  
```  
  
## パラメーター  
 `value`  
 必ず指定します。  変換される [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値 \(通常はオブジェクトまたは配列\)。  
  
 `replacer`  
 省略可能です。  結果を変換する関数または配列。  
  
 `replacer` が関数の場合、`JSON.stringify` は関数を呼び出して、各メンバーのキーと値を渡します。  元の値の代わりに戻り値が使用されます。  関数が `undefined` を返した場合、そのメンバーは除外されます。  ルート オブジェクトのキーは空の文字列 "" です。  
  
 `replacer` が配列の場合は、配列のキー値を持つメンバーのみが変換されます。  メンバーが変換される順序は配列のキーの順序と同じです。  `replacer` の配列は、`value` 引数も配列の場合には無視されます。  
  
 `space`  
 省略可能です。  戻り値の JSON テキストにインデント、空白文字、改行文字を追加して読みやすくします。  
  
 `space` を省略した場合、戻り値のテキストには空白が追加されずに生成されます。  
  
 `space` に数を指定すると、戻り値のテキストの各レベルは、指定した数の空白でインデントされます。  `space` が 10 を超える場合、テキストは 10 個の空白でインデントされます。  
  
 `space` が空でない文字列 \('\\ t' など\) の場合、戻り値のテキストの各レベルは、その文字でインデントされます。  
  
 `space` が 10 文字より長い文字列の場合は、最初の 10 文字が使用されます。  
  
## 戻り値  
 JSON テキストを表す文字列。  
  
## 例外  
  
|例外|状態|  
|--------|--------|  
|[置換引数が無効です](../../javascript/misc/invalid-replacer-argument.md)|`replacer` 引数が関数または配列ではない。|  
|[値引数の循環参照はサポートされていません。](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|`value` 引数に循環参照が含まれる。|  
  
## 解説  
 `value` に `toJSON` メソッドが含まれている場合、`JSON.stringify` 関数は、そのメソッドの戻り値を使用します。  `toJSON` メソッドの戻り値が `undefined` である場合、メンバーは変換されません。  これにより、オブジェクトは独自の JSON 表現を決定できます。  
  
 `undefined` などの JSON 表現のない値は変換されません。  それらは、オブジェクトではドロップされます。  配列では null と置き換えられます。  
  
 文字列値の先頭と末尾は引用符です。  円記号を使用してエスケープする必要がある文字を除くすべての Unicode 文字が引用符で囲まれている可能性があります。  次の文字の前には円記号を指定する必要があります。  
  
-   二重引用符 \("\)  
  
-   円記号 \(\\\)  
  
-   バックスペース \(b\)  
  
-   フォーム フィード \(f\)  
  
-   改行 \(n\)  
  
-   キャリッジ リターン \(r\)  
  
-   水平タブ \(t\)  
  
-   4 桁の 16 進数値 \(uhhhh\)  
  
## 実行の順序  
 シリアル化プロセス中に、`toJSON` メソッドが `value` 引数に存在する場合、`JSON.stringify` は、最初に `toJSON` メソッドを呼び出します。  存在しない場合は、元の値が使用されます。  次に、`replacer` 引数が指定されている場合、値 \(元の値または `toJSON` の戻り値\) は、`replacer` 引数の戻り値と置き換えられます。  最後に、省略可能な `space` 引数に基づいて値に空白が追加され、最終的な JSON のテキストが生成されます。  
  
## 使用例  
 この例では、`JSON.stringify` を使用して、`contact` オブジェクトを JSON テキストに変換します。  `memberfilter` 配列は、`surname` メンバーと `phone` メンバーのみを変換するように定義されています。  `firstname` メンバーは省略されます。  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Array();  
memberfilter[0] = "surname";  
memberfilter[1] = "phone";  
var jsonText = JSON.stringify(contact, memberfilter, "\t");  
document.write(jsonText);  
// Output:   
// { "surname": "Aaberg", "phone": [ "555-0100", "555-0120" ] }  
```  
  
## 使用例  
 この例では、配列を指定した `JSON.stringify` を使用します。  `replaceToUpper` 関数は、配列の各文字列を大文字に変換します。  
  
```javascript  
var continents = new Array();  
continents[0] = "Europe";  
continents[1] = "Asia";  
continents[2] = "Australia";  
continents[3] = "Antarctica";  
continents[4] = "North America";  
continents[5] = "South America";  
continents[6] = "Africa";  
  
var jsonText = JSON.stringify(continents, replaceToUpper);  
  
function replaceToUpper(key, value) {  
    return value.toString().toUpperCase();  
}  
  
//Output:  
// "EUROPE,ASIA,AUSTRALIA,ANTARCTICA,NORTH AMERICA,SOUTH AMERICA,AFRICA"  
  
```  
  
## 使用例  
 この例では、`toJSON` メソッドを使用して、文字列値を大文字に変換します。  
  
```javascript  
var contact = new Object();   
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
document.write(jsonText);  
  
// Output:  
{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}  
  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## 必要条件  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## 参照  
 [JSON.parse 関数](../../javascript/reference/json-parse-function-javascript.md)   
 [toJSON メソッド \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [フィード リーダーのサンプル アプリ \(Windows Store\)](http://code.msdn.microsoft.com/Feed-reader-sample-99d68cf8)