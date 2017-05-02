---
title: "constructor プロパティ (Boolean) | Microsoft Docs"
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor プロパティ (Boolean)
ブール値を作成する関数を指定します。  
  
## 構文  
  
```  
  
boolean.constructor([[value])  
```  
  
#### パラメーター  
 `boolean`  
 ブール値の名前を指定します。  
  
 `value`  
 省略可能です。  ブール値を指定します。  1 または 0、あるいは "true" または "false" の文字列です。  
  
## 解説  
 `constructor` プロパティには、Boolean オブジェクトのインスタンスを作成する関数への参照が格納されます。  
  
## 使用例  
 constructor プロパティの使用例を次に示します。  
  
```javascript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]