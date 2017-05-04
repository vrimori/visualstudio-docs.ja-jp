---
title: "toString メソッド (エラー) | Microsoft Docs"
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString メソッド (エラー)
エラーを表す文字列を返します。  
  
## 構文  
  
```  
  
error.toString()  
```  
  
## パラメーター  
 `date`  
 必須です。  文字列として表示するエラーを指定します。  
  
## 戻り値  
 「Error: 」およびエラー メッセージを返します。  
  
## 使用例  
 エラーを指定した `toString` メソッドの使用例を次に示します。  
  
```javascript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]