---
title: "instanceof 演算子 (JavaScript) | Microsoft Docs"
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
  - "instanceof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "instanceOf 演算子"
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# instanceof 演算子 (JavaScript)
オブジェクトが特定のクラスのインスタンスかどうかを示すブール値を返します。  
  
## 構文  
  
```  
  
result = object instanceof class  
```  
  
## パラメーター  
 `result`  
 必須。  任意の変数。  
  
 `object`  
 必須。  任意のオブジェクト式を指定します。  
  
 `class`  
 必須。  任意の定義済みオブジェクト クラス。  
  
## 解説  
 `instanceof` 演算子は、`object` が `class` のインスタンスである場合に `true` を返します。  オブジェクトのプロトタイプ チェーンに `class` が存在する場合は、`true` を返します。  `object` が `class` のインスタンスではない場合、または `object` が `null` の場合は `false` を返します。  
  
## 使用例  
 `instanceof` 演算子を使用する方法の例を次に示します。  
  
```javascript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## 必要条件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 参照  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)