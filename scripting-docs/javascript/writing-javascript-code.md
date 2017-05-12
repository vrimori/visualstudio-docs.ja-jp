---
title: "JavaScript コードの記述 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.htmldesigner.html"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "コード, JavaScript 構文"
  - "コメント, JavaScript コード"
  - "JavaScript コード"
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# JavaScript コードの記述
他の多くのプログラミング言語と同様に、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] はステートメントおよび関連する一連のステートメントとコメントのブロックで構成されます。  ステートメント内では、変数、文字列、数値、および式を使用できます。  
  
## ステートメント  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] プログラムは、ステートメントのコレクションです。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ステートメントでは、1 つの完全なタスクを実行するように式を組み合わせます。  
  
 ステートメントには、1 つ以上の式、キーワード、または演算子 \(記号\) が含まれます。  一般に、ステートメントは単一行に記述しますが、複数行に記述することもできます。  複数のステートメントをセミコロンで区切って同じ行に記述することもできます。  一般に、新しい行は新しいステートメントで始まります。  ステートメントは、明示的に終了することをお勧めします。  ステートメントを明示的に終了するには、ステートメントの最後にセミコロン \(;\) を記述します。[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、セミコロン \(;\) は終了文字を表します。  
  
 次に [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ステートメントの例を 2 つ示します。  \/\/ 文字の後の文は、プログラムを解説する*コメント*です。  
  
```javascript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 中かっこ \({}\) で囲まれた一連の [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ステートメントは、*ブロック*と呼ばれます。  ブロック内にまとめられたステートメントは、一般に 1 つのステートメントとして扱われます。  つまり、単一のステートメントを記述できる場所であれば、ほとんどの場合、代わりにブロックを使用できます。  ただし、**for** ループと `while` ループのヘッダーは例外です。  ブロック内の各ステートメントはセミコロンで終了しますが、ブロックそのものはセミコロンで終了しません。  
  
 ブロックは、一般に関数と条件処理で使用します。  C\+\+ およびその他の一部の言語とは異なり、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ではブロックは新しいスコープとは見なされません。新しいスコープを作成するのは関数だけです。  
  
 `else` 句に中かっこで囲まれた 2 つのステートメント ブロックが含まれる例を次に示します。  ブロックは、単一のステートメントとして扱われます。  関数自体は、中かっこで囲まれたステートメントのブロックで構成されます。  関数の下のステートメントはブロックの外部にあるので、関数の定義には含まれません。  
  
```javascript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## コメント  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の単一行コメントは、2 つのスラッシュ \(\/\/\) で始まります。  単一行のコメントの例を次に示します。  
  
```javascript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 複数行コメントは、スラッシュとアスタリスク \(\/\*\) で始まり、この 2 つを逆に組み合わせた記号 \(\*\/\) で終わります。  
  
```javascript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  複数行コメントを他の複数行コメント内に単純に埋め込んだ場合、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では正しく解釈されません。  埋め込んだ複数行コメントの終わりを示す \*\/ が、複数行コメント全体の終わりとして解釈されてしまうからです。  これは、埋め込んだ複数行コメント以降のテキストがコメント アウトされずに [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] コードとして解釈され、構文エラーが発生することを意味します。  
  
 コメントを記述する場合は、単一行コメントのブロックとして記述することをお勧めします。  これにより、複数行コメントを使って、コードの大きなセグメントを後からコメント アウトできます。  
  
```javascript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## 代入と等価  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ステートメントでは、変数に値を代入するために等号 \(\=\) が使用されています。これは、代入演算子です。  \= 演算子の左側のオペランドは常に左辺値です。  左辺値の例を次に示します。  
  
-   変数  
  
-   配列要素  
  
-   オブジェクトのプロパティ  
  
 \= 演算子の右側のオペランドは常に右辺値です。  右辺値には、式の値を含むあらゆる型の任意の値を指定できます。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の代入ステートメントの例を次に示します。  
  
```javascript  
var anInteger = 3;  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] コンパイラは、このステートメントを "**anInteger** 変数に 3 という値を代入する"、または "**anInteger** が 3 という値を受け取る" と解釈します。  
  
 代入演算子 \(\=\) と等値演算子 \(\=\=\) の違いを理解してください。  2 つの値を比較して等しいかどうかを確認する場合は、2 つの等号 \(\=\=\) を使用します。  これについては、「[Controlling Program Flow \(プログラム フロー制御\)](../javascript/controlling-program-flow-javascript.md)」で詳しく説明します。  
  
## 式  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の式の値には、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の任意の有効な型 \(数値、文字列、オブジェクトなど\) を指定できます。  最も簡単な式はリテラルです。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] のリテラルの式の例を次に示します。  
  
```javascript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 より複雑な式には、変数、関数呼び出し、およびその他の式を含めることができます。  式を組み合わせて、演算子を使用する複雑な式を作成できます。  演算子には、`+` \(加算\)、`-` \(減算\)、`*` \(乗算\)、`/` \(除算\) などがあります。  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の複雑な式の例を次に示します。  
  
```javascript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```