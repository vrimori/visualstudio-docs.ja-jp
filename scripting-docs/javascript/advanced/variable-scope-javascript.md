---
title: "変数のスコープ (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "スコープ、JavaScript"
  - "変数のスコープ [JavaScript]"
  - "変数、スコープ [JavaScript]"
ms.assetid: a811a9a6-856f-46e9-8be3-f2d22a0c245f
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# 変数のスコープ (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] には、グローバルとローカルの 2 つのスコープがあります。  関数定義の外部で宣言された変数はグローバル変数になり、プログラム内のどこからでも値の参照や変更を行うことができます。  関数定義内で宣言された変数はローカル変数になります。  ローカル変数は、関数が実行されるたびに作成され破棄されます。関数の外部のコードからローカル変数にアクセスすることはできません。  JavaScript では、ブロック スコープ変数の特殊な場合を除いて、\(中かっこで囲んで \(`{. . .}`\) 新しいスコープを定義する\) ブロック スコープはサポートしていません。  
  
## JavaScript のスコープ  
 ローカル変数にはグローバル変数と同じ名前を付けることができます。同じ名前を付けても、2 つの変数は完全に区別されます。一方の変数の値を変更しても、もう一方の変数には影響しません。  ローカル変数は、そのローカル変数が宣言されている関数の内部だけで意味を持ちます。  
  
```javascript  
// Global definition of aCentaur.  
var aCentaur = "a horse with rider,";  
  
// A local aCentaur variable is declared in this function.  
function antiquities(){  
  
   var aCentaur = "A centaur is probably a mounted Scythian warrior";  
}  
  
antiquities();  
aCentaur += " as seen from a distance by a naive innocent.";  
  
document.write(aCentaur);  
  
// Output: "a horse with rider, as seen from a distance by a naive innocent."  
```  
  
 JavaScript の変数は、それが存在するスコープの先頭で宣言されたものとして評価されます。  この動作により、次に示すような予期しない結果となる場合があります。  
  
```javascript  
var aNumber = 100;  
tweak();  
  
function tweak(){  
  
    // This prints "undefined", because aNumber is also defined locally below.  
    document.write(aNumber);  
  
    if (false)  
    {  
        var aNumber = 123;    
    }  
}  
```  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、関数を実行するときに、まずすべての変数宣言 \(例: `var someVariable;` など\) を探します。  次に、`undefined` の初期値を使用して変数が作成されます。  値を指定して変数が宣言されている場合でも \(例: `var someVariable = "something";`\)、その値は最初は `undefined` であり、宣言を含む行が実行されたときに初めて宣言された値を受け取ります。  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、宣言が条件ブロック内にあるか他の構造内にあるかに関係なく、コードの実行前にすべての変数宣言が処理されます。  すべての変数が検出されると、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は関数内のコードを実行します。  変数が関数内で暗黙的に宣言されている場合、つまり、`var` を使用して宣言されていない変数が代入式の左側にある場合、その変数はグローバル変数として作成されます。  
  
 JavaScript では、内側 \(入れ子\) の関数には、関数から制御が戻った後でも、関数自体と同じスコープに存在するローカル変数への参照が格納されています。  このような参照のセットは、クロージャと呼ばれます。  次の例では、内部関数への 2 回目の呼び出しで、1 回目の呼び出しと同じメッセージ \("Hello Bill"\) が出力されます。これは、外部関数の入力パラメーター `name` が、内部関数のクロージャに格納されるローカル変数であるためです。  
  
```javascript  
function send(name) {  
    // Local variable 'name' is stored in the closure  
    // for the inner function.  
    return function () {  
        sendHi(name);  
    }  
}  
  
function sendHi(msg) {  
    console.log('Hello ' + msg);  
}  
  
var func = send('Bill');  
func();  
// Output:  
// Hello Bill  
sendHi('Pete');  
// Output:  
// Hello Pete  
func();  
// Output:  
// Hello Bill  
```  
  
## ブロック スコープ変数  
 Internet Explorer 11 では、ブロック スコープ変数である [let](../../javascript/reference/let-statement-javascript.md) および [const](../../javascript/reference/const-statement-javascript.md) のサポートが導入されています。  これらの変数では、中かっこ \(`{. . .}`\) で新しいスコープを定義します。  これらの変数のいずれかを特定の値に設定した場合、設定を行ったスコープのみに、その値が適用されます。  
  
 `let` およびブロック スコープの使用例を次に示します。  
  
> [!NOTE]
>  次のコードは、Internet Explorer 11 標準モード以降でサポートされます。  
  
```javascript  
let x = 10;  
var y = 10;  
{  
    let x = 5;  
    var y = 5;  
    {  
        let x = 2;  
        var y = 2;  
        document.write("x: " + x + "<br/>");  
        document.write("y: " + y + "<br/>");  
        // Output:  
        // x: 2  
        // y: 2  
    }  
    document.write("x: " + x + "<br/>");  
    document.write("y: " + y + "<br/>");  
    // Output:  
    // x: 5  
    // y: 2  
}  
  
document.write("x: " + x + "<br/>");  
document.write("y: " + y + "<br/>");  
// Output:  
// x: 10  
// y: 2  
```