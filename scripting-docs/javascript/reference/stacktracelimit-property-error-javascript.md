---
title: "stackTraceLimit プロパティ (Error) (JavaScript) | Microsoft Docs"
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
  - "Error.stackTraceLimit"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "エラー スタックのトラック制限 [JavaScript]"
  - "JavaScript エラー スタック"
  - "エラー スタック [JavaScript]"
  - "JavaScript スタック トレース制限"
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# stackTraceLimit プロパティ (Error) (JavaScript)
表示するエラー フレームの数と等しいスタック トレースの制限を取得または設定します。  既定の制限は 10 です。  
  
## 構文  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## 解説  
 `stackTraceLimit` プロパティに設定できる値は、0 から `Infinity` までの正の値です。  エラーがスローされたときに `stackTraceLimit` プロパティが 0 に設定されていた場合は、スタック トレースは表示されません。  プロパティが負の値または数値以外の値に設定される場合、値は 0 に変換されます。  stackTraceLimit が `Infinity` に設定されている場合は、そのスタック全体が表示されます。  それ以外の場合は、`ToUint32` を使用して値が変換されます。  
  
## 使用例  
 スタック トレースの制限を設定してから取得する方法を次の例に示します。  
  
```javascript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## 必要条件  
 Internet Explorer 10 と [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでサポートされます。  
  
 **対象**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## 参照  
 [description プロパティ \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message プロパティ \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name プロパティ \(Error\)](../../javascript/reference/name-property-error-javascript.md)   
 [stack プロパティ \(Error\)](../../javascript/reference/stack-property-error-javascript.md)