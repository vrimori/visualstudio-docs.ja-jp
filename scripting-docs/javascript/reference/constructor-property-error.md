---
title: "constructor プロパティ (エラー) | Microsoft Docs"
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
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor プロパティ (エラー)
エラーを作成する関数を指定します。  
  
## 構文  
  
```  
  
error.constructor  
```  
  
## 解説  
 `error` 引数は必須で、エラー オブジェクトの名前を指定します。  
  
 `constructor` プロパティは、プロトタイプを持つあらゆるオブジェクトのプロトタイプのメンバーです。  `constructor` プロパティには、特定のオブジェクトのインスタンスを作成する関数への参照が格納されます。  
  
## 使用例  
 constructor プロパティの使用例を次に示します。  
  
```javascript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]