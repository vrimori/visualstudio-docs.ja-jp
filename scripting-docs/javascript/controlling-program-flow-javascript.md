---
title: "プログラム フローの制御 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean values, program flow
- continue statement
- break statement
- control flow, about control flow
ms.assetid: 4ef58c82-e5d6-4b09-9458-cf0aa3b39bf5
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20c256d26c6991067d7c25c0c835eda6e5e5aac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="controlling-program-flow-javascript"></a>プログラム フローの制御 (JavaScript)
通常、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] スクリプトのステートメントは、記述された順に次々に実行されます。 これはシーケンシャル実行と呼ばれ、プログラム フローの既定の方法です。  
  
 シーケンシャル実行の代わりに、プログラム フローをスクリプトの他の部分に移動する方法があります。 つまり、シーケンスに従って次のステートメントを実行する代わりに、他のステートメントが実行されます。  
  
 有用なスクリプトにするためには、このコントロールの移動を論理的な方法で行う必要があります。 プログラム制御の移動は、真理値ステートメント (戻り値がブール値の **true** または **false**) で表される判断の結果に基づきます。 式を作成した後、結果が true かどうかを評価します。 このためのプログラムの構造には、主に 2 つの種類があります。  
  
 1 番目は選択構造です。 これを使用すると、プログラムに分岐点を作成してプログラム フローの流れを変更できます。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、次の 4 つの選択構造を使用できます。  
  
-   単一選択構造 (**if**)  
  
-   分岐選択構造 (**if/else**)  
  
-   インライン三項演算子 (`?:`)  
  
-   複数選択構造 (`switch`)  
  
 プログラムの制御構造の 2 番目の種類は、反復構造です。 ある条件が true の間、アクションを繰り返すよう指定する場合に使用します。 制御ステートメントの条件が満たされると (通常は指定した反復処理の後)、制御は反復構造を抜けて次のステートメントに移ります。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、次の 4 つの反復構造を使用できます。  
  
-   ループの最初に式が評価される (`while`)  
  
-   ループの最後に式が評価される (**do/while**)  
  
-   オブジェクトの各プロパティを処理する (**for/in**)  
  
-   カウンターを使って反復を制御する (**for**)  
  
 選択制御構造と反復制御構造を入れ子やスタックにすることで、かなり複雑なスクリプトも作成できます。  
  
 構造化されたプログラム フローの 3 番目の形式は、例外処理を使用する方法ですが、このドキュメントでは取り上げません。  
  
## <a name="using-conditional-statements"></a>条件付きステートメントの使用  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、条件付きステートメントとして **if** および [if...else](../javascript/reference/if-dot-dot-dot-else-statement-javascript.md) がサポートされています。 **if** ステートメントでは、条件が評価され、条件が満たされた場合は、関連する [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] コードが実行されます。 `if...else` ステートメントでは、条件が満たされなかった場合は別のコードが実行されます。 単純な **if** ステートメントでは全体を 1 行に収めて記述することもできますが、通常は、**if** ステートメントや `if...else` ステートメントが複数行にわたって記述されます。  
  
 **if** ステートメント、および `if...else` ステートメントを使用したコードの例を次に示します。 最初の例は、ブール値の評価の最も単純な形式です。 かっこで囲まれた部分の評価結果が **true** である (または true に変換できる) 場合にだけ、**if** の後のステートメントまたはステートメント ブロックが実行されます。  
  
```JavaScript  
function GetReaction(newShip, color, texture, dayOfWeek)  
{  
   // The test succeeds if the newShip Boolean value is true.  
   if (newShip)  
   {  
      return "Champagne Bottle";  
   }  
  
   // The test succeeds if both conditions are true.  
   if (color == "deep yellow" && texture == "large and small wrinkles")  
   {  
      return "Is it a crenshaw melon?";  
   }  
  
   // The test succeeds if either condition is true.  
   if ((dayOfWeek == "Saturday") || (dayOfWeek == "Sunday"))  
   {  
      return "I'm off to the beach!";  
   }  
   else  
   {  
      return "I'm going to work.";  
   }  
}  
  
var reaction = GetReaction(false, "deep yellow", "smooth", "Sunday");  
document.write(reaction);  
  
// Output: I'm off to the beach!  
```  
  
## <a name="conditional-operator"></a>条件演算子  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、暗黙的な条件形式もサポートしています。 これは、(条件の前に単語の **if** を付けるのではなく) 評価する条件の後に疑問符を付けます。 また、2 種類の式を指定し、条件を満たした場合に一方を、満たさなかった場合にもう一方を使用します。 これらの代替式はコロンで区切る必要があります。  
  
```JavaScript  
var AMorPM = (theHour >= 12) ? "PM" : "AM";  
```  
  
 複数の条件を組み合わせて評価する場合、その中に結果を予測できる条件が含まれるときは、ショート サーキット評価と呼ばれる機能を使用できます。これにより、スクリプトの実行を高速化できます。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] で論理式を評価する場合は、結果を得るために必要な最低限の部分式だけが評価されます。  
  
 たとえば、((x == 123) && (y == 6)) という AND 式がある場合、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、まず x が 123 かどうかがチェックされます。 そうでない場合は、y が 6 であっても、式全体が true になることはありません。 したがって、y の評価は行われず、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] によって **false** 値が返されます。  
  
 同様に、複数の条件のうち 1 つでも **true** になればよい (&#124;&#124; 演算子を使用) 場合は、いずれかの条件が満たされた直後に評価が終了します。 これは、評価する条件に関数の呼び出しや複雑な式が含まれている場合などに効果的です。 この点に留意して、OR 式を記述する場合は、**true** になる可能性が最も高い条件を最初に配置します。 AND 式を記述する場合は、**false**になる可能性が最も高い条件を最初に配置します。  
  
 この方法でスクリプトを作成している利点は、たとえば次のコードでは **runfirst()** が 0 を返す場合に **runsecond()** が実行されないことです。  
  
```JavaScript  
if ((runfirst() == 0) || (runsecond() == 0)) {  
    // some code  
}  
```  
  
## <a name="using-loops"></a>ループの使用  
 1 つのステートメント、または一連のステートメントを繰り返し実行する方法がいくつか用意されています。 一般に、繰り返し実行は "*ループ*" または "*反復処理*" と呼ばれます。 反復処理では、ループを 1 回実行します。 通常、ループの制御は、ループ内が実行されるたびに値が変化する変数を評価して行います。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、[for](../javascript/reference/for-statement-javascript.md) ループ、[for...in](../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) ループ、[while](../javascript/reference/while-statement-javascript.md) ループ、[do...while](../javascript/reference/do-dot-dot-dot-while-statement-javascript.md) ループの 4 種類のループがサポートされています。  
  
## <a name="using-for-loops"></a>for ループの使用  
 **for** ステートメントは、カウンター変数、評価する条件、およびカウンターを更新する処理を指定します。 ループが反復処理される前に、条件が評価されます。 評価が成功した場合は、ループ内のコードが実行されます。 評価が成功しなかった場合、ループ内のコードは実行されず、ループ後の 1 行目のコードの処理が続けられます。 カウンター変数は、ループの実行後、次の反復処理が開始される前に更新されます。  
  
 ループの条件が満たされない場合、ループは一度も実行されません。 条件が常に満たされると、無限ループになります。 場合によっては、ループが実行されない方が望ましいこともありますが、無限ループが望ましい場合はほとんどありません。したがって、ループ条件を記述するときには注意が必要です。  
  
```JavaScript  
// The update expression ("icount++" in the following examples)  
// is executed at the end of the loop, after the block of  
// statements that forms the body of the loop is executed, and  
// before the condition is tested.  
  
// Set a limit of 10 on the loop.  
var howFar = 10;  
  
// Create an array called sum with 10 members, 0 through 9.  
var sum = new Array(howFar);  
sum[0] = 0;  
  
// Iterate from 0 through 9.  
var theSum = 0;  
for(var icount = 0; icount < howFar; icount++)  
{  
   theSum += icount;  
   sum[icount] = theSum;  
}  
  
// This code is not executed at all, because icount is not greater than howFar.  
var newSum = 0;  
for(var icount = 0; icount > howFar; icount++)  
{  
   newSum += icount;  
}  
  
// This is an infinite loop.  
var sum = 0;  
for(var icount = 0; icount >= 0; icount++)  
{  
   sum += icount;  
}  
```  
  
## <a name="using-forin-loops"></a>for...in ループの使用  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] には、[オブジェクト](../javascript/objects-and-arrays-javascript.md)内のすべてのユーザー定義プロパティ、または配列内のすべての要素をステップ実行するための特殊なループが用意されています。 `for...in` ループのループ カウンターは、数値ではなく文字列です。 これには、現在のプロパティの名前、または現在の配列要素のインデックスが含まれています。  
  
```JavaScript  
// Create an object with some properties  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 1234";  
  
// Enumerate (loop through)_all the properties in the object  
for (var prop in myObject)  
{  
    // This displays "The property 'name' is James", etc.  
    document.write("The property '" + prop + "' is " + myObject[prop]);  
    // New line.  
    document.write("<br />");    
}  
```  
  
 `for...in` ループは VBScript の `For Each...Next` ループに似ていますが、動作は異なります。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の **for...in ループ**では [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] オブジェクトのプロパティが反復処理されます。 VBScript の **For Each...Next** ループは、コレクションの項目を反復処理します。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] でコレクションをループ処理するには、[Enumerator オブジェクト](../javascript/reference/enumerator-object-javascript.md)を使うか、存在する場合はコレクション オブジェクトの `forEach` メソッドを使う必要があります。 Internet Explorer のオブジェクトのような一部のオブジェクトでは、VBScript の **For Each...Next** ループと、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の **for...in** ループの両方をサポートしていますが、ほとんどのオブジェクトはそうではありません。  
  
## <a name="using-while-loops"></a>while ループの使用  
 `while` ループは、**for** ループに似ています。 ただし、`while` ループには組み込みのカウンター変数がなく、式も更新しない点が異なります。 1 つのステートメントや一連のステートメントの繰り返し実行を制御する場合で、単純に "このコードを n 回実行する" というよりも複雑な規則が必要なときは、`while` ループを使用します。 次の例では、Internet Explorer のオブジェクト モデルと `while` ループを使用してユーザーに単純な質問をしています。  
  
```JavaScript  
var x = 0;  
while ((x != 5) && (x != null))  
{  
    x = window.prompt("What is my favorite number?", x);  
}  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
> [!NOTE]
>  `while` ループには、明示的に組み込まれたカウンター変数がありません。このため、他の種類のループと比べ、無限ループに陥る可能性が高くなります。 さらに、`while` ループは、ループを制御する条件がいつどこで更新されるのかを見つけにくいため、条件が更新されないループを記述する可能性もあります。 このような理由から、`while` ループをデザインするときには注意が必要です。  
  
 上で説明したように、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] には **do...while** ループもあります。これは、while ループに似ていますが、条件がループの先頭ではなく末尾で評価されるためループが少なくとも 1 回は実行されます。 上のコード例は、次のように記述することもできます。  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
} while ((x != 5) && (x != null));  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
## <a name="using-break-and-continue-statements"></a>break ステートメントと continue ステートメントの使用  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、[break](../javascript/reference/break-statement-javascript.md) ステートメントは、ある条件を満たしたときにループの実行を終了するために使われます。 **break** は、`switch` ブロックを終了するときにも使います。 [continue](../javascript/reference/continue-statement-javascript.md) ステートメントを使うと、コード ブロックの残りの部分を実行せずに、次の反復処理に移ることができます。ループが **for** または `for...in` の場合は、カウンター変数が更新されます。  
  
 次の例は、前の例を基にしており、**break** ステートメントと **continue** ステートメントを使ってループを制御します。  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
  
    // Did the user cancel? If so, break out of the loop  
    if (x == null)  
        break;  
  
    // Did they enter a number?  
    // If so, no need to ask them to enter a number.  
    if (Number(x) == x)  
        continue;  
  
    // Ask user to only enter in numbers  
    window.alert("Please only enter in numbers!");  
  
} while (x != 5)  
  
if (x != 5)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```