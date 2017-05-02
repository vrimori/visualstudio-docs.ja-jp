---
title: "Regular Expression オブジェクト (JavaScript) | Microsoft Docs"
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
  - "RegularExpression_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp オブジェクト, 概要"
  - "Regular Expression オブジェクト"
  - "正規表現, RegExp オブジェクト"
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Regular Expression オブジェクト (JavaScript)
正規表現パターンとそのパターンを適用する方法を示すフラグとを含むオブジェクト。  
  
## 構文  
  
```  
re = /pattern/[flags]  
```  
  
## 構文  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## パラメーター  
 *re*  
 必須。  正規表現パターンが割り当てられている変数の名前。  
  
 *pattern*  
 必須。  使用する正規表現パターン。  構文 1 を使用する場合、「\/」文字でパターンを区切ります。  構文 2 を使用する場合、パターンを引用符で囲みます。  
  
 `flags`  
 省略可能です。  構文 2 を使用する場合、フラグを引用符で囲みます。  組み合わせることもできる、使用可能なフラグは次のとおりです。  
  
-   g \(*pattern* のすべての出現箇所のグローバル検索\)  
  
-   i \(大文字小文字を区別しない\)  
  
-   m \(複数行の検索\)  
  
-   u \(Unicode\)、EcmaScript 6 の [Unicode 機能](../../javascript/advanced/special-characters-javascript.md)を有効にします。  [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] でのみサポートされています。  
  
-   y \(付箋一致\)、正規表現の `lastIndex` プロパティで一致を検索します \(それ以降のインデックスでは検索しません\)。  [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] でサポートされています。  
  
## 解説  
 **正規表現**オブジェクトをグローバル `RegExp` オブジェクトと混同しないでください。  同じように見えますが、それらは別個のオブジェクトです。  **正規表現**オブジェクトのプロパティには、1 つの特定の**正規表現**インスタンスに関する情報だけが含まれていますが、グローバル `RegExp` オブジェクトのプロパティには、それぞれの一致が生じるごとに継続的に更新される情報が含まれています。  
  
 **正規表現**オブジェクトには、文字列で文字の組み合わせを検索するときに使用されるパターンが格納されています。  **正規表現**オブジェクトが作成された後に、それが文字列メソッドに渡されるか、または文字列が正規表現メソッドのいずれかに渡されます。  実行された最新の検索についての情報は、グローバル `RegExp` オブジェクトに格納されます。  
  
 検索文字列があらかじめ分かっている場合には、構文 1 を使用します。  ユーザー入力から取得される文字列の場合など、検索文字列が頻繁に変更される場合や不明の場合には、構文 2 を使用します。  
  
 *pattern* 引数は、内部形式にコンパイルされてから使用されます。  構文 1 では、スクリプトが読み込まれる際に *pattern* がコンパイルされます。  構文 2 では、使用の直前または **コンパイル** メソッドが呼び出されるときに *pattern* がコンパイルされます。  
  
## 使用例  
 次の例は、正規表現パターンとその関連フラグとが含まれたオブジェクト \(re\) を作成することにより、**正規表現**オブジェクトの使用方法を例示しています。  この場合、結果として生じる**正規表現**オブジェクトは、その後 `match` メソッドによって使用されます。  
  
```javascript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## 使用例  
 次の例では、複数のインスタンスを検索するように正規表現パターンを更新します。  
  
```javascript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## 使用例  
 \/y フラグを使用するとき、一致が見つかった場合は、`lastindex` が最後の一致の後にある次の文字のインデックスに更新されます。  一致が見つからない場合は、`lastindex` が 0 にリセットされます。  
  
 次の例では、\/y フラグと `lastIndex` プロパティを使用して、特定のインデックス位置で一致するものを検索します。  
  
```javascript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## プロパティ  
 [global プロパティ](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [ignoreCase プロパティ](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [multiline プロパティ](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [source プロパティ](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## メソッド  
 [compile メソッド](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [exec メソッド](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [test メソッド](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 u フラグは [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] でサポートされています。  
  
 y フラグは [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] でサポートされています。  
  
## 参照  
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)