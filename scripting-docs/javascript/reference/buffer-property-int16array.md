---
title: "buffer プロパティ (Int16Array) | Microsoft Docs"
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
ms.assetid: 22117ad2-d865-47be-b15e-8181de257672
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# buffer プロパティ (Int16Array)
読み取り専用です。  この配列によって参照される ArrayBuffer を取得します。  
  
## 構文  
  
```javascript  
var arrayBuffer = int16Array.buffer;  
```  
  
## 使用例  
 配列の ArrayBuffer を取得する方法の例を次に示します。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int16Array(buffer.byteLength / 2);  
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]