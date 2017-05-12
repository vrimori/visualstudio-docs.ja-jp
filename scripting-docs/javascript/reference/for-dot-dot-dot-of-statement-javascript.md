---
title: "for...of ステートメント (JavaScript) | Microsoft Docs"
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# for...of ステートメント (JavaScript)
反復可能なオブジェクトから取得した反復子の値ごとに、1 つまたは複数のステートメントを実行します。  
  
## 構文  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## パラメーター  
 `variable`  
 必須です。  `object` の任意のプロパティ値を代入できる変数。  
  
 `object`  
 必須です。  `Array`、`Map`、`Set` などの反復可能オブジェクト、または[iterator インターフェイス](http://msdn.microsoft.com/ja-jp/3692355a-a703-4d43-8fb5-c03b4b7e8db1)を実装するオブジェクト。  
  
 `statements`  
 省略可能です。  `object` の値ごとに実行する 1 つ以上のステートメント。  複合ステートメントにすることもできます。  
  
## 解説  
 ループの各反復処理の最初で、`variable` の値は `object` の次のプロパティ値となります。  
  
## 使用例  
 次の例は、配列での `for...of` ステートメントの使用方法を示しています。  
  
```javascript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## 使用例  
 次の例は、`Map` オブジェクトでの `for...of` ステートメントの使用方法を示しています。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 参照  
 [for...in ステートメント](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)