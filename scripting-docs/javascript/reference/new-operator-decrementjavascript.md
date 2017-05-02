---
title: "new 演算子 (JavaScript) | Microsoft Docs"
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
  - "new_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript の new 演算子"
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# new 演算子 (JavaScript)
新しいオブジェクトを作成します。  
  
## 構文  
  
```  
new constructor ([arguments])   
```  
  
## パラメーター  
 `constructor`  
 必須です。  オブジェクトのコンストラクターを指定します。  コンストラクターが引数を受け取らない場合は、かっこを省略できます。  
  
 `arguments`  
 省略可能です。  新しいオブジェクトのコンストラクターに渡す任意の引数を指定します。  
  
## 解説  
 `new` 演算子は次のタスクを実行します。  
  
-   メンバーを持たないオブジェクトを作成します。  
  
-   新しく作成したオブジェクトへのポインターを `this` ポインターとして渡して、そのオブジェクトのコンストラクターを呼び出します。  
  
-   コンストラクターは、受け取った引数に従って、オブジェクトを初期化します。  
  
 **new** 演算子の有効な使用例を次に示します。  
  
```javascript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)