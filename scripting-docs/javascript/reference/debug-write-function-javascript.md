---
title: "Debug.write 関数 (JavaScript) | Microsoft Docs"
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
  - "Write"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "write メソッド [JavaScript]"
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Debug.write 関数 (JavaScript)
スクリプト デバッガーに文字列を送信します。  
  
## 構文  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## パラメーター  
 *str1、str2、...、strN*  
 省略可能です。  スクリプト デバッガーに送信する文字列を指定します。  
  
## 解説  
 `Debug.write` 関数は、実行時にスクリプト デバッガーのイミディエイト ウィンドウに文字列を送信します。  スクリプトがデバッグされない場合、`Debug.write` 関数の影響はありません。  
  
 `Debug.write` 関数は `Debug.writeln` 関数とほとんど同じです。  唯一の違いは `Debug.writeln` 関数が文字列を送信した後に改行文字を送信することです。  
  
## 使用例  
 `Debug.write` 関数を使用してスクリプト デバッガーのイミディエイト ウィンドウに変数の値を表示する例を次に示します。  
  
> [!NOTE]
>  この例を実行するには、スクリプト デバッガーをインストールし、スクリプトをデバッグ モードで実行する必要があります。  
>   
>  Internet Explorer 8 には、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] デバッガーが含まれています。  Internet Explorer の旧バージョンを使用する場合は、「[方法: Internet Explorer でスクリプトのデバッグを有効にして起動する](http://go.microsoft.com/fwlink/?LinkId=133801)」を参照してください。  
  
```javascript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Debug オブジェクト](../../javascript/reference/debug-object-javascript.md)  
  
## 参照  
 [Debug.writeln 関数](../../javascript/reference/debug-writeln-function-javascript.md)