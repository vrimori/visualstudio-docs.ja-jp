---
title: "replace メソッド (String) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "replace"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Replace メソッド"
  - "置換 (文字列を)"
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# replace メソッド (String) (JavaScript)
正規表現または検索文字列を使用して、文字列内のテキストを置換します。  
  
## 構文  
  
```  
  
stringObj. replace(rgExp, replaceText)  
```  
  
## パラメーター  
 `stringObj`  
 必須です。  置換対象となる `String` オブジェクトの名前またはリテラル文字列を指定します。  この文字列は、**replace** メソッドでは変更されません。  むしろ、このメソッドの戻り値が、置換によって生成される文字列です。  
  
 `rgExp`  
 必須です。  正規表現パターンおよび適用できるフラグを含む **Regular Expression** オブジェクトのインスタンスを指定します。  正規表現を表す `String` オブジェクトまたはリテラル文字列である場合もあります。  `rgExp` が **Regular Expression** オブジェクトのインスタンスでない場合は文字列に変換され、完全に一致する文字列の検索が実行されます。文字列から正規表現への変換は行われません。  
  
 `replaceText`  
 必須です。  `String` で、`rgExp` と一致した部分と置き換えるテキストを格納する `stringObj` オブジェクトまたはリテラル文字列を指定します。  [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降では、`replaceText` 引数で、置換するテキストを返す関数を指定することもできます。  
  
## 戻り値  
 **replace** メソッドは、指定された置換を終えた後の `stringObj` のコピーを返します。  
  
## 解説  
 次の表にある変数を使用して、最後に検出した一致やその文字列を指定できます。  一致変数は、テキストの置換処理において、対象を動的に指定する必要がある場合に使用します。  
  
|文字|意味|  
|--------|--------|  
|**$$**|`$` \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降\)|  
|**$&**|`stringObj` でパターンが完全に一致した部分を指定します。  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降\)|  
|`$``|`stringObj` の先頭から、**$&** が表す一致の直前までの部分を表します。  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降\)|  
|`$'`|`stringObj` の、**$&** が表す一致の直後から末尾までの部分を表します。  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降\)|  
|`$`  ***n***|サブ文字列の中で *n* 番目に検出されたものを取得します。*n* には、1 桁の 10 進数値 \(1 ～ 9\) を指定します。  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降\)|  
|`$`  ***nn***|サブ文字列の中で *nn* 番目に検出されたものを取得します。*nn* には 2 桁の 10 進数値 \(01 ～ 99\) を指定します。  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降\)|  
  
 `replaceText` が関数の場合、一致する各文字列に対してこの関数が *m* \+ 3 個の引数を伴って呼び出されます。*m* は、`rgExp` の中で使用されている取得を示す開きかっこの数です。  1 個目の引数は一致したサブ文字列です。  次の *m* 引数は、検索結果そのものです。  *m* \+ 2 個目の引数は、`stringObj` 内の一致した位置のオフセットを表し、*m* \+ 3 個目の引数は `stringObj` を表します。  結果は、該当する関数呼び出しの戻り値をそれぞれ一致する文字列と置換した文字列値で返されます。  
  
 **replace**メソッドを実行すると、グローバルなオブジェクト `RegExp` のプロパティが更新されます。  
  
## 使用例  
 すべての "the" を "a" に置換する **replace** メソッドの使用例を次に示します。  
  
```javascript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 さらに、**replace** メソッドでは、パターンに一致する文字列どうしを置換できます。  文字列の中の単語の各ペアを入れ替える例を次に示します。  
  
```javascript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumps lazy the dog.  
```  
  
 置換テキストを返す関数を使用する方法を次に示します。この例は [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降で動作します。  これは、摂氏変換によって、「F」に続くすべての数値のインスタンスを置き換えます。  
  
```javascript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [exec メソッド \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match メソッド \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [search メソッド \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test メソッド \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/ja-jp/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/ja-jp/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/ja-jp/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [HTML5 ドラッグ アンド ドロップのサンプル アプリ](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)