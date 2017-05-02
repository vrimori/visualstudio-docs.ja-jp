---
title: "JSON オブジェクト (JavaScript) | Microsoft Docs"
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
  - "JSON"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON オブジェクト"
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 43
---
# JSON オブジェクト (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の値と JSON \(JavaScript Object Notation\) 形式間で変換を行う関数を提供する組み込みオブジェクト。  `JSON.stringify` 関数は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値を JSON テキストにシリアル化します。  `JSON.parse` 関数は、JSON テキストを逆シリアル化して [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値を生成します。  
  
## 構文  
  
```  
  
JSON.[method]  
  
```  
  
## パラメーター  
 `Method`  
 必ず指定します。  `JSON` オブジェクトのいずれかのメソッドの名前。  
  
## 解説  
 `new` 演算子を使用して `JSON` オブジェクトを作成することはできません。  この操作を行うと、エラーが発生します。  ただし、`JSON` オブジェクトをオーバーライドするか、変更することはできます。  
  
 スクリプト エンジンは、エンジンが読み込まれるときに `JSON` オブジェクトを作成します。  このメソッドは、スクリプト内でいつでも使用できます。  
  
 組み込みの `JSON` オブジェクトを使用するには、スクリプトで定義されている別の `JSON` オブジェクトでそれをオーバーライドしていないことを確認します。  `JSON` オブジェクトの存在を検出する既存のスクリプト ステートメントでは評価が異なるため、これらのステートメントの変更が必要になる場合があります。  このコード例を次に示します。  
  
```javascript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 前の例では、`!this.JSON` が、[!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)] では false と評価します。  したがって、`if` ステートメント内のコードは実行されません。  
  
## 関数  
 [JSON.parse 関数](../../javascript/reference/json-parse-function-javascript.md)  
  
 [JSON.stringify 関数](../../javascript/reference/json-stringify-function-javascript.md)  
  
## 必要条件  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## 参照  
 [toJSON メソッド \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [JavaScript オブジェクト](../../javascript/reference/javascript-objects.md)   
 [ハブ テンプレートのサンプル アプリ \(Windows Store\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)