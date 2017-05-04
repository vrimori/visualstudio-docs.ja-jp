---
title: "Spread 演算子 (...) (JavaScript) | Microsoft Docs"
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
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Spread 演算子 (...) (JavaScript)
配列リテラルの一部を \(別の配列リテラルなどの\) 反復可能な式から初期化したり、式を \(関数呼び出しで\) 複数の引数に拡張したりできます。  
  
## 構文  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## パラメーター  
 `iterable`  
 必須。  反復可能オブジェクト。  
  
 `arg0ToN`  
 省略可能です。  配列リテラルの 1 つ以上の要素。  
  
 `args`  
 省略可能です。  関数への 1 つ以上の引数。  
  
## 解説  
 反復子について詳しくは、「[反復子とジェネレーター](../../javascript/advanced/iterators-and-generators-javascript.md)」を参照してください。  rest パラメーターとして spread 演算子を使用する方法について詳しくは、「[関数](../../javascript/functions-javascript.md)」を参照してください。  
  
## 使用例  
 次のコード例では、spread 演算子と `concat` メソッドの使用法が対比されています。  
  
```javascript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## 使用例  
 次のコード例は、関数呼び出しで spread 演算子を使用する方法について示しています。  この例では 2 つの配列リテラルが、spread 演算子を使用する関数に渡され、配列が複数の引数に拡張されます。  
  
```javascript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## 使用例  
 spread 演算子を使用すると、これまでは `apply` を使用する必要があったコードを簡略化できます。  
  
```javascript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
func.apply(this, args);  
// New method  
func(...args);  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 参照  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)