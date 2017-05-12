---
title: "compile メソッド (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "compile"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Compile メソッド"
  - "コンパイル (ソース コードを), 正規表現"
  - "正規表現, コンパイル"
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# compile メソッド (Regular Expression) (JavaScript)
実行を高速化するために、正規表現を内部形式にコンパイルします。  
  
## 構文  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## パラメーター  
 `rgExp`  
 必須です。  **Regular Expression** オブジェクトのインスタンスを指定します。  変数名またはリテラルです。  
  
 *pattern*  
 必須です。  コンパイルする正規表現パターンを格納した文字列式を指定します。  
  
 `flags`  
 省略可能です。  指定できるフラグは、次のとおりです。結合もできます。  
  
-   g \(*pattern* 引数に指定したパターンと一致する文字列をすべて検索するグローバル検索\)  
  
-   i \(大文字小文字を区別しない\)  
  
-   m \(複数行検索\)  
  
## 解説  
 **compile** メソッドは、検索の実行を高速化するために、引数 *pattern* に指定したパターンを内部形式に変換します。  これにより、たとえばループ内などで、正規表現をより効率よく使用できるようになります。  正規表現をコンパイルすると、繰り返し同じ表現を使用する場合に処理が速くなります。  ただし、正規表現を変更すると使用できなくなります。  
  
## 使用例  
 **compile** メソッドの使用例を次に示します。  
  
```javascript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 参照  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)