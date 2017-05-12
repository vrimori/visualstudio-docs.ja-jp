---
title: "description プロパティ (Error) (JavaScript) | Microsoft Docs"
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
  - "Description"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Description プロパティ"
  - "エラー処理, エラーの説明"
  - "エラー, 記述"
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# description プロパティ (Error) (JavaScript)
特定のエラーに関連付けられたエラーを説明する文字列を設定または返します。  
  
## 構文  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## パラメーター  
 *object*  
 必須です。  `Error` オブジェクトの任意のインスタンスを指定します。  
  
 `stringExpression`  
 省略可能です。  エラーの説明を含む文字列表現を指定します。  
  
## 解説  
 **description** プロパティは、特定のエラーに関連付けられたエラー メッセージを格納する文字列です。  このプロパティを使用して、エラーをユーザーに通知します。  
  
 **description** プロパティと **message** プロパティの機能は同じです。**description** プロパティは下位互換性を提供し、**message** プロパティは ECMA 規格に準拠しています。  
  
## 使用例  
 **description** プロパティの使用例を次に示します。  
  
```javascript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **対象**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## 参照  
 [number プロパティ \(Error\)](../../javascript/reference/number-property-error-javascript.md)   
 [message プロパティ \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name プロパティ \(Error\)](../../javascript/reference/name-property-error-javascript.md)