---
title: "Debug.writeln 関数 (JavaScript) | Microsoft Docs"
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
  - "writeln"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "writeIn メソッド"
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Debug.writeln 関数 (JavaScript)
スクリプト デバッガーに文字列とそれに続く改行文字を送信します。  
  
## 構文  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## パラメーター  
 *str1、str2、...、strN*  
 省略可能です。  スクリプト デバッガーに送信する文字列を指定します。  
  
## 解説  
 `Debug.writeln` 関数は、実行時に Microsoft Script Debugger のイミディエイト ウィンドウに文字列とそれに続く改行文字を送信します。  スクリプトがデバッグされない場合、`Debug.writeln` 関数の影響はありません。  
  
 `Debug.writeln` 関数は `Debug.write` 関数とほとんど同じです。  唯一の違いは `Debug.write` 関数が文字列を送信した後に改行文字を送信しないことです。  
  
## 使用例  
 `Debug.writeln` 関数を使用して Microsoft Script Debugger のイミディエイト ウィンドウに変数の値を表示する例を次に示します。  
  
> [!NOTE]
>  この例を実行するには、スクリプト デバッガーをインストールし、スクリプトをデバッグ モードで実行する必要があります。  
>   
>  Internet Explorer 8 には、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] デバッガーが含まれています。  Internet Explorer の旧バージョンを使用する場合は、「[方法: Internet Explorer でスクリプトのデバッグを有効にして起動する](http://go.microsoft.com/fwlink/?LinkId=133801)」を参照してください。  
  
```javascript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Debug オブジェクト](../../javascript/reference/debug-object-javascript.md)  
  
## 参照  
 [Debug.write 関数](../../javascript/reference/debug-write-function-javascript.md)