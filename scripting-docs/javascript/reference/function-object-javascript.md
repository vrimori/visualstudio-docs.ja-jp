---
title: "Function オブジェクト (JavaScript) | Microsoft Docs"
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
  - "function"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Function オブジェクト"
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Function オブジェクト (JavaScript)
新しい関数を作成します。  
  
## 構文  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## 構文  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## パラメーター  
 `functionName`  
 必須です。  新規作成された関数の名前を指定します。  
  
 `argname1...argnameN`  
 省略可能です。  関数が受け取る引数のリストを指定します。  
  
 `body`  
 省略可能です。  関数が呼び出されたときに実行する [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] コード ブロックを記述した文字列を指定します。  
  
## 解説  
 関数は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の基本データ型です。  構文 1 では、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] が必要に応じて `Function` オブジェクトに変換する関数値を作成します。  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は、関数を呼び出す際に、構文 2 で作成した `Function` オブジェクトを関数値に変換します。  
  
 構文 1 は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で新しい関数を作成する標準的な方法です。  構文 2 は、関数オブジェクトを明示的に作成するために使用する代替手段です。  
  
 たとえば、渡された 2 つの引数を追加する関数を宣言するには、この 2 つのいずれかの方法を使用できます。  
  
## 例 1  
  
```javascript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## 例 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 どちらの場合にも、次のようなコード行を使用して関数を呼び出します。  
  
```javascript  
add(2, 3);  
```  
  
> [!NOTE]
>  関数を呼び出すときは、必須の引数とかっこを必ず記述してください。  かっこを付けずに関数を呼び出すと、関数の戻り値ではなく、関数そのものが返されます。  
  
## プロパティ  
 [0...  
          n プロパティ](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[arguments プロパティ](../../javascript/reference/arguments-property-function-javascript.md) &#124; [callee プロパティ](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [caller プロパティ](../../javascript/reference/caller-property-function-javascript.md) &#124; [constructor プロパティ](../../javascript/reference/constructor-property-object-javascript.md) &#124; [length プロパティ \(Function\)](../../javascript/reference/length-property-function-javascript.md) &#124; [prototype プロパティ](../../javascript/reference/prototype-property-object-javascript.md)  
  
## メソッド  
 [apply メソッド](../../javascript/reference/apply-method-function-javascript.md) &#124; [bind メソッド](../../javascript/reference/bind-method-function-javascript.md) &#124; [call メソッド](../../javascript/reference/call-method-function-javascript.md) &#124; [toString メソッド](../../javascript/reference/tostring-method-object-javascript.md) &#124; [valueOf メソッド](../../javascript/reference/valueof-method-object-javascript.md)  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 参照  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)   
 [new 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var ステートメント](../../javascript/reference/var-statement-javascript.md)