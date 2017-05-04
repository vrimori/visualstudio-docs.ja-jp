---
title: "データ型 (JavaScript) | Microsoft Docs"
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
  - "Boolean データ型, サポートされているデータ型"
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 35
---
# データ型 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] には、3 つのプライマリ データ型、2 つの複合データ型、および 2 つの特別なデータ型があります。  
  
## プライマリ データ型  
 プライマリ \(プリミティブ\) データ型は次のとおりです。  
  
-   String  
  
-   Number  
  
-   Boolean  
  
## 複合データ型  
 複合 \(参照\) データ型は次のとおりです。  
  
-   Object  
  
-   Array  
  
## 特別なデータ型  
 特別なデータ型は次のとおりです。  
  
-   Null  
  
-   未定義  
  
## 文字列型 \(String\)  
 文字列値は、0 個以上の Unicode 文字 \(英字、数字、および区切り記号\) をつなぎ合わせたものです。  文字列型は、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] でテキストを表すために使用します。  スクリプトで文字列リテラルを使用するには、単一引用符 \('\) または二重引用符 \("\) で囲みます。  単一引用符で囲んだ文字列の内側で二重引用符を使用することも、二重引用符で囲んだ文字列の内側で単一引用符を使用することもできます。  文字列の例を次に示します。  
  
```javascript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] には単一の文字を表す型がないことに注意してください。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] で単一の文字を表す場合は、1 文字だけで構成される文字列を作成します。  何も入っていない文字列 \(""\) は、空の文字列 \(長さ 0 の文字列\) です。  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] にはエスケープ シーケンスが用意されており、直接入力できない文字を文字列として使用できます。  たとえば、`\t` はタブ文字を指定します。  詳細については、「[特殊文字](../javascript/advanced/special-characters-javascript.md)」を参照してください。  
  
## Number 型  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、整数値と浮動小数点値の間に違いはありません。[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の数値はどちらを表すこともできます \([!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、内部的にすべての数値が浮動小数点値として表されます\)。  
  
### 整数値  
 整数値は、正の整数、負の整数、および 0 です。  これらの数値は、基数 10 \(10 進数\)、基数 16 \(16 進数\)、および基数 8 \(8 進数\) で表現できます。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、ほとんどの数値は 10 進数で表現されます。  
  
 16 進数 \("hex"\) の整数であることを示すには、先頭に "0x" \(ゼロと x \(大文字でも小文字でも可\)\) を付けます。  各桁には 0 ～ 9 の数字および A ～ F の英字 \(大文字でも小文字でも可\) を使用します。  A ～ F の英字は、1 桁の数値として 10 進数の 10 ～ 15 を表すために使用します。  たとえば、0xF は 15、0x10 は 16 に相当します。  
  
 8 進数の整数であることを示すには、先頭に "0" \(ゼロ\) を付けます。  各桁には 0 ～ 7 の数字だけを使用します。  先頭が "0" でも "8" や "9" が含まれている場合は 10 進数として処理されます。  
  
 8 進数および 16 進数で負の値を表すことはできますが、小数部分はなく、指数表記は使用できません。  
  
> [!NOTE]
>  [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)] より、[parseInt 関数](../javascript/reference/parseint-function-javascript.md)は、プレフィックスが "0" の文字列を 8 進数として処理しません。  ただし、`parseInt` 関数を使用しない場合は、プレフィックスが "0" の文字列を 8 進数として解釈することもできます。  
  
### 浮動小数点値  
 浮動小数点値には、整数部分と小数部分があります。  また、指数表記も使用できます。  10 の累乗の指数を表すには、大文字または小文字の "e" を使用します。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は、8 バイトの IEEE 754 浮動小数点標準を使用して数値を表現します。  つまり、5x10<sup>-324</sup> から 1.79769x10<sup>308</sup> までの数値を記述できます。  小数点があり、小数点の前に "0" がある数値は、10 進浮動小数点数として解釈されます。  
  
 数値が "0x" または "00" で始まり小数点がある場合は、エラーが発生します。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の数値の例を次に示します。  
  
|Number|説明|10 進数での表記|  
|------------|--------|---------------|  
|.0001、0.0001、1e\-4、1.0e\-4|この 4 つの浮動小数点数は、すべて同じ値です。|0.0001|  
|3.45e2|浮動小数点数。|345|  
|45|整数。|45|  
|0378|整数。  "0" で始まるため 8 進数のように見えますが、8 は 8 進数では使用できない数値であるため、10 進数として処理されます。|378|  
|0377|8 進数です。  上記の数値より 1 だけ小さい数値に見えますが、実際にはまったく異なる数値です。|255|  
|0.0001|浮動小数点数。  "0" で始まりますが小数点があるため 8 進数ではありません。|0.0001|  
|00.0001|エラーが発生します。  先頭の 2 つのゼロは 8 進数を表しますが、8 進数に小数部分を含めることはできません。|N\/A \(コンパイラ エラー\)|  
|0Xff|16 進数の整数です。|255|  
|0x37CF|16 進数の整数です。|14287|  
|0x3e7|16 進数の整数です。  'e' は指数演算として処理されません。|999|  
|0x3.45e2|エラーが発生します。  16 進数は小数部を持つことができません。|N\/A \(コンパイラ エラー\)|  
  
 さらに、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] には特殊な値を持つ数値があります。  これらの数値は、次のとおりです。  
  
-   NaN \(非数値\)。  数値演算が不適切なデータ \(文字列や未定義値\) で実行された場合に使用されます。  
  
-   正の無限大。  正の数値が [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] で表記するには大きすぎる場合に使用されます。  
  
-   負の無限大。  負の数値が [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] で表記するには大きすぎる場合に使用されます。  
  
-   正の 0 および負の 0。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、正のゼロと負のゼロが区別されます。  
  
## Boolean 型  
 文字列型および数値型では、ほぼ無限とも言える種類の値を利用できるのに対し、Boolean 型で使用できる数値は 2 種類だけです。  それは、`true` と `false` のリテラルです。  ブール値は真偽値で、条件が true であるかどうかを指定します。  
  
 スクリプト内で行った比較の結果は、常にブール値となります。  次の [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] コード行があるとします。  
  
```javascript  
y = (x == 2000);  
```  
  
 ここでは、変数 `x` の値が数値 2000 と等しいかどうかが評価されます。  等しい場合、比較の結果はブール値の **true** になり、これが変数 `y` に代入されます。  `x` が 2000 に等しくない場合、比較の結果はブール値の `false` になります。  
  
 ブール値は、制御構造において特に便利です。  次のコードでは、ブール値を作成する比較を、それを使用するステートメントと直接結合しています。  次の [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] コードを例に取ります。  
  
```javascript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の `if/else` ステートメントは、ブール値が `true` \(`z = z + 1`\) の場合に 1 つのアクションを実行し、ブール値が `false` \(`x = x + 1`\) の場合に別のアクションを実行します。  
  
 比較式としては、任意の式を使用できます。  0、null、undefined、または空の文字列に評価される式は、すべて `false` として解釈されます。  その他の値に評価される式は、`true` として解釈されます。  たとえば、次のような式を使用した場合を考えます。  
  
```javascript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 上のコードは、単一の等号 \(代入演算子\) が使用されているため、`x` が `y + z` に等しいかどうかを調べているのではありません。  上のコードは、`y + z` の値を変数 `x` に代入し、その式の結果 \(`x` の値\) がゼロかどうかを確認しています。  `x` が `y + z` に等しいかどうかを調べるには、次のコードを使用する必要があります。  
  
```javascript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 比較の詳細については、「[Controlling Program Flow \(プログラム フロー制御\)](../javascript/controlling-program-flow-javascript.md)」を参照してください。  
  
## Null 型  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の `null` 型には、null という値が 1 つだけあります。  `null` キーワードは、関数または変数の名前として使用できません。  
  
 `null` を含む変数には有効な数値、文字列、ブール値、配列、またはオブジェクトが含まれません。  `null` 値を代入することによって、変数自体は削除せずに、変数の内容を消去できます。  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、C や C\+\+ と異なり、`null` は 0 と等価ではありません。  また、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の `typeof` 演算子では、`null` 値は `null` 型ではなく `Object` 型として扱われます。  この処理は混乱を招く可能性がありますが、下位互換性のために残されています。  
  
## Undefined 型  
 `undefined` 値は、存在しないオブジェクト プロパティを使用した場合や、宣言されている一方で値が代入されていない変数を使用した場合に返されます。  
  
 変数を `undefined` と比較することによって変数が存在するかどうかを調べることができます。また、変数の型を文字列 "undefined" と比較することによって、変数の型が `undefined` かどうかを調べることができます。  次の例では、変数 `x` が宣言されているかどうかを調べています。  
  
```javascript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 さらに、未定義の値を `null` と比較することもできます。  この比較は、プロパティ `someObject.prop` が `null` の場合、またはプロパティ `someObject.prop` が存在しない場合に `true` になります。  
  
```javascript  
someObject.prop == null;  
```  
  
 オブジェクトのプロパティが存在するかどうかを調べるには、**in** 演算子を使用できます。  
  
```javascript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## 参照  
 [オブジェクトと配列](../javascript/objects-and-arrays-javascript.md)   
 [typeof 演算子](../javascript/reference/typeof-operator-decrementjavascript.md)