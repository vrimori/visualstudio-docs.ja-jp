---
title: "valueOf メソッド (エラー) | Microsoft Docs"
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf メソッド (エラー)
エラーの文字列値を返します。  
  
## 構文  
  
```  
  
error.valueOf()  
```  
  
#### パラメーター  
 `error` オブジェクトは、Error の任意のインスタンスです。  
  
## 戻り値  
 文字列 "Error: " およびエラー メッセージを返します。  
  
## 使用例  
 日付を指定した `valueOF` メソッドの使用例を次に示します。  
  
```javascript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]