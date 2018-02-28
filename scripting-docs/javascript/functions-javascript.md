---
title: "関数 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- intrinsic JavaScript functions
ms.assetid: e2a72b5a-3edd-43d8-95e8-91721b38c1c1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7275985d07f9f564dac98ba39e5ec31618dcaac4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="functions-javascript"></a>関数 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 関数はアクションを実行します。また、値を返すこともできます。 場合によって、これらは計算や比較の結果です。 関数は、「グローバル メソッド」とも呼ばれます。  
  
 関数は 1 つの名前の下にいくつかの操作を結合します。 これにより、コードを効率化できます。 一連のステートメントをセットとして書き出して、それに名前を付け、それを呼び出して必要な情報を渡すことにより、そのセット全体を実行できます。  
  
 情報をかっこで囲み、関数の名前の後に指定することで、関数に情報を渡します。 関数に渡される情報は、引数やパラメーターと呼ばれます。 引数を使用しない関数もあれば、1 つまたは複数の引数を使用する関数もあります。 一部の関数では、その関数の使用方法によって引数の数が異なります。  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は 2 つの種類の関数をサポートしています。言語に組み込まれている関数と、ユーザーが独自に作成する関数です。  
  
## <a name="built-in-functions"></a>組み込み関数  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 言語には、いくつかの組み込み関数が含まれています。 式や特殊文字を処理するための関数もあれば、文字列を数値に変換する関数もあります。  
  
 これらの組み込み関数について詳しくは、「[JavaScript メソッド](../javascript/reference/javascript-methods.md)」をご覧ください。  
  
## <a name="creating-your-own-functions"></a>ユーザー独自の関数の作成  
 独自の関数を作成し、それらを必要に応じて使用することができます。 関数定義は、関数ステートメントと [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ステートメントのブロックとで構成されます。  
  
 以下の例に示されている **CheckTriplet** 関数は、その引数として三角形の辺の長さを取ります。 それら 3 つの数値がピタゴラスの三角形 (直角三角形の斜辺の長さの 2 乗は、他の 2 つの辺の長さの 2 乗の合計に等しい) を構成するかどうかをチェックして、その三角形が直角三角形がかどうかを計算します。 checkTriplet 関数は、他の 2 つの関数のいずれかを呼び出して、実際のテストを行います。  
  
 このテストの浮動小数点版では、テスト変数として非常に小さい数 ("epsilon") を使用していることに注意してください。 浮動小数点の計算には不確定要素や丸め誤差が伴うため、問題の 3 つの数値が整数であると分かっている場合を除いて、それら 3 つの数値がピタゴラスの三角形を構成するかどうかを直接テストすることは実際的ではありません。 直接のテストがより正確であるため、この例に示されているコードでは、そのテストが適切かどうかを判別して、適切な場合にそれを使用します。  
  
```JavaScript  
var epsilon = 0.00000000001; // Some very small number to test against.  
  
// The test function for integers.  
function integerCheck(a, b, c)   
{  
   // The test itself.  
   if ( (a*a) == ((b*b) + (c*c)) )     
      return true;  
  
   return false;  
} // End of the integer checking function.  
  
// The test function for floating-point numbers.  
function floatCheck(a, b, c)     
{  
   // Make the test number.  
   var delta = ((a*a) - ((b*b) + (c*c)))  
  
   // The test requires the absolute value  
   delta = Math.abs(delta);  
  
   // If the difference is less than epsilon, then it's pretty close.  
   if (delta < epsilon)     
      return true;  
  
   return false;  
} // End of the floating-poing check function.  
  
// The triplet checker.   
function checkTriplet(a, b, c)  
{   
   // Create a temporary variable for swapping values  
   var d = 0;   
  
   // First, move the longest side to position "a".  
  
   // Swap a and b if necessary  
   if (b > a)  
   {  
      d = a;  
      a = b;  
      b = d;  
   }  
  
   // Swap a and c if necessary  
   if (c > a)  
   {  
      d = a;  
      a = c;  
      c = d;  
   }  
  
   // Test all 3 values. Are they integers?  
   if (((a % 1) == 0) && ((b % 1) == 0) && ((c % 1) == 0))  
   {   
      // If so, use the precise check.  
      return integerCheck(a, b, c);   
   }  
   else  
   {  
      // If not, get as close as is reasonably possible.  
      return floatCheck(a, b, c);   
   }  
} // End of the triplet check function.  
  
// The next three statements assign sample values for testing purposes.  
var sideA = 5;  
var sideB = 5;  
var sideC = Math.sqrt(50.001);  
  
// Call the function. After the call, 'result' contains the result.  
var result = checkTriplet(sideA, sideB, sideC);  
```  
  
<a name="Arrow"></a>   
## <a name="arrow-functions"></a>アロー関数  
 アロー関数の構文 `=>` は、匿名関数を指定するための簡略化された方法を提供します。 アロー関数の構文は次のとおりです。  
  
```JavaScript  
([arg] [, arg]) => {  
    statements  
}  
```  
  
 アローの左側の値 (かっこで囲まれていることもある) は、関数に渡す引数を示しています。 関数に渡す引数が 1 つの場合には、かっこは必要ありません。 引数を渡さない場合には、かっこが必要です。 アローの右側の関数定義は、`v + 1` のような式、または中かっこ ({}) で囲まれた一連のステートメントとすることができます。  
  
> [!IMPORTANT]
>  アロー関数構文は、[!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] でのみサポートされています。  
  
 `new` 演算子はアロー関数と共に使用できません。  
  
 次のコード例は、アロー関数を式と共に関数定義として使用する方法を示しています。 最初の例では、v が引数として式に渡されます。 2 番目の例では、v と i が引数として式に渡されます。  
  
```  
var evens = [2, 4, 6, 8];  
  
// Using standard syntax.  
var odds = evens.map(function(v) { return v + 1; });  
  
// Using arrow function syntax.  
// Add one to each value to produce output.  
var odds = evens.map(v => v + 1);  
  
// The following line of code adds the index value to the passed  
// in value to produce output.  
// Note: the second argument to the callback function in the map   
// method is the index value (i).  
var nums = evens.map((v, i) => v + i);  
  
console.log(odds);  
console.log(nums);  
  
// Output:  
// [object Array] [3, 5, 7, 9]  
// [object Array] [2, 5, 8, 11]  
```  
  
 以下のコード例では、アロー関数を ステートメントのブロックと共に使用する方法を示します。  
  
```JavaScript  
var fives = new Array();  
  
// Statement block, re-using nums array from previous example.  
// Note: The first argument to the callback function in forEach  
// is the value of the array element (v).  
nums.forEach(v => {  
  if (v % 5 === 0)  
    fives.push(v);  
});  
  
console.log(fives);  
  
// Output:  
// [object Array] [5]  
```  
  
 標準の関数とは異なり、アロー関数は、同じ構文 `this` オブジェクトを前後のコードとして共有します。これを使用することにより、`var self = this;` などの回避策は必要なくなります。  
  
 次の例では、アロー関数内の `this` オブジェクトの値が、前後のコードの場合と同じであることを示しています (引き続き `bob` 変数を参照します)。  
  
```JavaScript  
var bob = {  
  _name: "Bob",  
  _friends: ["Pete", "Joe", "Larry"],  
  printFriends() {  
    this._friends.forEach(f =>  
      console.log(this._name + " knows " + f));  
  }  
}  
  
// Output:  
// Bob knows Pete  
// Bob knows Joe  
// Bob knows Larry  
```  
  
 アロー関数は、前後のコードと同じ構文 `arguments` オブジェクトも (`this` オブジェクトと同様に) 共有します。  
  
<a name="Default"></a>   
## <a name="default-parameters"></a>既定のパラメーター  
 初期値を割り当てることによって、関数のパラメーターに既定値を指定できます。 既定値には、定数値または式を指定できます。  
  
> [!IMPORTANT]
>  既定のパラメーターは、[!INCLUDE[jsv12textExp](../javascript/includes/jsv12textexp-md.md)] でのみサポートされています。  
  
 次の例で、y の既定値は 10、z の既定値は 20 です。 呼び出し元が 2 番目の引数として別個の値 (または未定義) を渡さななけば、関数では y の値として 10 が使用されます。 呼び出し元が 3 番目の引数として別個の値 (または未定義) を渡さななけば、関数では z の値として 20 が使用されます。  
  
```JavaScript  
var val = 20;  
  
function f(x, y=10, z=val) {  
  return x + y + z;  
}  
  
console.log(f(3));  
console.log(f(3, 3));  
console.log(f(3, 3, 3));  
  
// Output:  
// 33  
// 26  
// 9  
```  
  
<a name="Rest"></a>   
## <a name="rest-parameters"></a>rest パラメーター  
 spread 演算子 `...` によって指定された rest パラメーターを使うと、関数呼び出しの連続する引数を配列に変換できます。  
  
 rest パラメーターにより、`arguments` オブジェクトは必要なくなります。 rest パラメーターは、いくつかの点で `arguments` オブジェクトと異なります。以下に例を示します。  
  
-   rest パラメーターは実際の配列インスタンスなので、配列で実行できる操作をサポートしています。  
  
-   rest パラメーターには、別個の名前付き引数としては渡されない連続する引数のみが含まれています (これに対して、`arguments` オブジェクトには関数に渡されるすべての引数が含まれています)。  
  
> [!IMPORTANT]
>  rest パラメーターと spread 演算子は、[!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] でのみサポートされています。  
  
 次のコード例では、「hello」と「true」が配列値として渡され、y パラメーターに格納されます。 rest パラメーターは、関数の最後のパラメーターでなければなりません。  
  
```JavaScript  
function f(x, ...y) {  
  // y is an array.  
  return x * y.length;  
}  
  
console.log(f(3, "hello", true));  
  
// Output:  
// 6  
  
```  
  
 spread 演算子のその他の使用方法については、「[spread 演算子](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [JavaScript 言語リファレンス](../javascript/javascript-language-reference.md)