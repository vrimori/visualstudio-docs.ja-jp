---
title: 反復子とジェネレーター (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68ef5b2f-0349-492b-b557-73ff2a2f90cf
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a566e870c6e9589daed86d42e3fb933374cbb17
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="iterators-and-generators-javascript"></a>反復子とジェネレーター (JavaScript)
反復子は、リストのようなコンテナー オブジェクトを走査するのに使用されるオブジェクトです。 JavaScript において、反復子オブジェクトは個別の組み込みオブジェクトではなく、`next` メソッドを実装することでコンテナー オブジェクト内の次の項目にアクセスするオブジェクトです。  
  
 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] では、独自のカスタム反復子を作成することができます。 ただし、通常はジェネレーターを使用するとはるかに簡単になります。ジェネレーターは、反復子の作成を大幅に簡素化します。 ジェネレーターは、一種の関数であり、反復子のファクトリです。 ジェネレーター関数を使用してカスタム反復子を作成する場合は、「[ジェネレーター](#Generators)」を参照してください。  
  
> [!CAUTION]
>  ジェネレーターは [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] でサポートされています。  
  
## <a name="iterators"></a>Iterators  
 JavaScript 反復子を実装するには、特定のインターフェイスに準拠した 2 つまたは 3 つのオブジェクトが必要です。  
  
-   反復可能なインターフェイス  
  
-   反復子インターフェイス  
  
-   IteratorResult インターフェイス  
  
 これらのインターフェイスを使用して、カスタム反復子を作成できます。 そうした場合、`for…of` ステートメントを使用して反復可能なオブジェクトを走査できるようになります。  
  
### <a name="iterable-interface"></a>反復可能なインターフェイス  
 反復可能なインターフェイスは、反復可能なオブジェクト (反復子を取得できるオブジェクト) で必要なインターフェイスです。 たとえば、`for (let e of C)` の `C` では、反復可能なインターフェイスを実装する必要があります。  
  
 反復可能なオブジェクトは、反復子を返す Symbol.iterator メソッドを提供する必要があります。  
  
```JavaScript  
obj[Symbol.iterator] = function() { return iterObj; }  
```  
  
 このプロパティは、引数を取らず、`Iterator` インターフェイスに準拠したオブジェクト (`iterObject`) を返す関数とする必要があります。  
  
 配列など組み込み型の多くは、反復可能になりました。 `for…of` ループは、反復可能なオブジェクトを使用します  (ただし、すべての組み込み型の反復可能なオブジェクトが反復子であることは限りません。 たとえば、Array オブジェクト自体は反復子ではありませんが、反復可能です。ArrayIterator も反復可能です)。  
  
### <a name="iterator-interface"></a>反復子インターフェイス  
 Symbol.iterator メソッドによって返されるオブジェクトは、`next` メソッドを実装する必要があります。 `next` メソッドの構文は次のとおりです。  
  
```JavaScript  
iterObj.next() = function() { return iterResultObj; };  
```  
  
 `next` メソッドは、値を返す関数です。 この関数は、`IteratorResult` インターフェイスに準拠したオブジェクト (`iterResultObj`) を返します。 反復子の `next` メソッドの前の呼び出しで、`done` プロパティが True である `IteratorResult` オブジェクトが返された場合、反復は終了し、`next` メソッドは再び呼び出されません。  
  
 反復子に `return` メソッドを含めることで、スクリプトが反復子で終了する場合に、反復子が正しく配置されていることを確認することもできます。  
  
### <a name="iteratorresult-interface"></a>IteratorResult インターフェイス  
 IteratorResult インターフェイスは、反復子で `next` メソッドの結果を得るために必要なインターフェイスです。 `next` によって返されるオブジェクトは、`done` および `value` プロパティを提供する必要があります。  
  
```JavaScript  
var iterResultObj = { done: true|false, value: value }  
```  
  
 `done` プロパティは、反復子の `next` メソッドの呼び出しの状態 (True または False) を返します。 反復子の最後に到達した場合、`done` は True を返します。 最後に到達していない場合、`done` は false を返して、値が使用可能となります。 `done` プロパティ (プロパティ自体または継承されたプロパティ) が存在しない、`done` の結果は False と見なされます。  
  
 `done` が False の場合、`value` プロパティは、現在の反復要素の値を返します。 `done` が True の場合、戻り値が指定されていれば、反復子の戻り値が返されます。 反復子が戻り値を持たない場合、`value` は定義されません。 その場合、`value` プロパティは、明示的な value プロパティを継承していなければ、適合するオブジェクトに存在しない可能性があります。  
  
<a name="Generators"></a>   
## <a name="generators"></a>ジェネレーター  
 カスタム反復子の作成および使用を容易にするには、関数*構文と 1 つまたは複数の `yield` 式を使用してジェネレーター関数を作成します。 ジェネレーター関数は、ジェネレーター関数本体の実行を可能にする反復子 (すなわち、ジェネレーター) を返します。 この関数は、次の `yield` または `return` ステートメントまで実行します。  
  
 反復子の `next` メソッドを呼び出して、ジェネレーター関数から次の値を返します。  
  
 次の例に、文字列オブジェクトの反復子を返すジェネレーターを示します。  
  
```JavaScript  
function* stringIter() {  
    var str = "bobsyouruncle";  
    var idx = 0;  
    while(idx < str.length)  
        yield str[idx++];  
}  
  
var si = stringIter();  
  
console.log(si.next().value);  
console.log(si.next().value);  
console.log(si.next().value);  
  
// Output:  
// b  
// o  
// b  
  
```  
  
 ジェネレーターの yield オペランド式は、`next` への呼び出しを終了し、2 つのプロパティを持つ `IteratorResult` オブジェクトを返します。2 つのプロパティとは、`done` (`done=false`) と `value` (`value=operand`) です。 `operand` はオプションです。存在しないままにしておくと、値は定義されません。  
  
 ジェネレーターの `return` ステートメントは、`done=true` と value プロパティのオプションのオペランド結果を含む `IteratorResult` を返して、ジェネレーターを終了します。  
  
 `yield` の代わりに `yield*` 式を使用して、別のジェネレーターへ、または配列や文字列などの別の反復可能なオブジェクトへデリゲートすることもできます。  
  
 前の例に以下のコードを追加した場合、`yield*` は `stringIter` ジェネレーターにデリゲートします。  
  
```JavaScript  
function* strIter() {  
    yield "jo";  
    yield* stringIter();  
}  
  
var si2 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
  
// Output:  
// jo  
// b  
// o  
// b  
```  
  
 `next` に引数を渡し、その引数を使用してジェネレーターの状態を変更することで、より高度なジェネレーターを作成することもできます。 `next` は、以前に実行した `yield` 式の結果値となります。 次の例では、`next` メソッドに値 100 を渡すときに、ジェネレーターの内部インデックス値をリセットします。  
  
```  
function* strIter() {  
    var str = "jobob";  
    var idx = 0;  
    while(idx < str.length) {  
        var modify = yield str[idx++];  
        if(modify == 100) {  
            idx = 0;  
        }  
    }
}
  
var si3 = strIter();  
  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next(100).value);  
  
// Output:  
// j  
// o  
// b  
// j  
  
```  
  
 他の高度なジェネレーターで、ジェネレーターの `throw` メソッドを呼び出すことができます。 スローされたエラーは、ジェネレーターが一時停止したポイント (次の `yield` ステートメントの前) でスローされているように見えます。
