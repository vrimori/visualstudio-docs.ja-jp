---
title: "Object.assign 関数 (Object) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Object.assign 関数 (Object) (JavaScript)
1 つ以上のソース オブジェクトからターゲット オブジェクトに値をコピーします。  
  
## 構文  
  
```  
Object.assign(target, ...sources );  
```  
  
#### パラメーター  
 `target`  
 必須です。  列挙可能なプロパティのコピー先となるオブジェクト。  
  
 `...sources`  
 必須です。  列挙可能なプロパティのコピー元となる 1 つ以上のオブジェクト。  
  
## 例外  
 割り当てエラーがある場合、この関数は `TypeError` をスローして、コピー操作が終了します。  ターゲット プロパティが書き込み不可の場合、`TypeError` がスローされます。  
  
## 解説  
 この関数はターゲット オブジェクトを返します。  *列挙可能な独自の*プロパティだけが、ソース オブジェクトからターゲット オブジェクトにコピーされます。  この関数を使用して、オブジェクトを結合したりそのクローンを作成したりすることができます。  
  
 `null` や `undefined` ソースは、空のオブジェクトのように扱われ、ターゲット オブジェクトに影響を与えません。  
  
## 使用例  
 次のコード例では、`Object.assign` を使用してオブジェクトを結合する方法を示します。  
  
```javascript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## 使用例  
 次の例では、`Object.assign` を使用してオブジェクトのクローンを作成する方法を示します。  
  
```javascript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]