---
title: "findIndex メソッド (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# findIndex メソッド (Array) (JavaScript)
コールバック関数で指定したテスト条件を満たしている最初の配列の値のインデックス値を返します。  
  
## 構文  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### パラメーター  
 `arrayObj`  
 必須です。  Array オブジェクト。  
  
 `callbackfn`  
 必須です。  配列の各要素をテストするコールバック関数。  
  
 `thisArg`  
 省略可能です。  コールバック関数で `this` オブジェクトを指定します。  指定しない場合、`this` オブジェクトは定義されません。  
  
## 解説  
 `findIndex` は、配列の各要素に対して、要素が `true` を返すまで昇順にコールバック関数を 1 回呼び出します。  要素が true を返すとすぐに、`findIndex` は true を返した要素のインデックス値を返します。  配列内のすべての要素が true を返さない場合、`findIndex` は \-1 を返します。  
  
 `findIndex` は配列オブジェクトを変更しません。  
  
## コールバック関数の構文  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(value, index, thisArg)`  
  
 コールバック関数は、パラメーターを 3 つまで使用して宣言できます。  
  
 コールバック関数のパラメーターは次のとおりです。  
  
|コールバック引数|定義|  
|--------------|--------|  
|`value`|配列要素の値。|  
|`index`|配列要素の数値インデックス。|  
|`arrayObj`|走査する配列オブジェクト。|  
  
## 使用例  
 次の例では、コールバック関数が、配列内の各要素が 2 と等しいかどうかをテストします。  
  
```javascript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## 使用例  
 次の例では、各要素をテストするために矢印構文を使用します。  この例では、`true` を返す要素がなく、`findIndex` は \-1 を返します。  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]