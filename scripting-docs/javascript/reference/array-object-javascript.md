---
title: "Array オブジェクト (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Array
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- constructor property
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a48d0ab5bac9d532e8fe8e356f4ea4df9e377b02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="array-object-javascript"></a>Array オブジェクト (JavaScript)
任意のデータ型の配列を作成する手段を提供します。  
  
## <a name="syntax"></a>構文  
  
```
arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayObj`  
 必須です。 `Array` オブジェクトを代入する変数名を指定します。  
  
 `size`  
 省略可能です。 配列のサイズ。 JScript の配列のインデックスは 0 から始まります。したがって、作成された要素のインデックスは 0 ～ (`size` - 1) となります。  
  
 `element0,...,elementN`  
 省略可能です。 配列に代入する要素を指定します。 配列が作成 *n*  + 1 個の要素、および`length`の *n*  + 1 です。 この構文を使用する場合は、複数の要素を指定する必要があります。  
  
## <a name="remarks"></a>コメント  
 配列の作成後に各要素にアクセスするには、[] 表記を使用します。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の配列は 0 から始まることに注意してください。  
  
```JavaScript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 符号なしの 32 ビット整数を `Array` コンストラクターに渡して、配列のサイズを指定できます。 値が負または非整数の場合は、実行時エラーが発生します。 次のコードを実行すると、コンソールにこのエラーが表示されます。  
  
```JavaScript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 `Array` オブジェクトのコンストラクターに単一値が渡され、それが数値でない場合、`length` プロパティは 1 に設定され、唯一の要素の値は渡された単一の引数の値になります。  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 JavaScript の配列は疎配列であり、配列内のすべての要素にデータが含まれるとは限りません。 JavaScript では、実際にデータを含む要素だけが配列に存在します。 このため、配列が使用するメモリ量を抑えることができます。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 次の一覧にあるメンバーの一部は、それ以降のバージョンで導入されています。 詳細については、次を参照してください。[バージョン情報](../../javascript/reference/javascript-version-information.md)または個々 のメンバーに関するドキュメントです。  
  
## <a name="properties"></a>プロパティ  
 `Array` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[constructor プロパティ](../../javascript/reference/constructor-property-array.md)|配列を作成する関数を指定します。|  
|[length プロパティ (Array)](../../javascript/reference/length-property-array-javascript.md)|配列内で定義されている最後の要素のインデックスより 1 だけ大きい整数値を返します。|  
|[prototype プロパティ](../../javascript/reference/prototype-property-array.md)|配列のプロトタイプへの参照を返します。|  
  
## <a name="functions"></a>関数  
 `Array` オブジェクトの関数を次の表に示します。  
  
|関数|説明|  
|--------------|-----------------|  
|[Array.from 関数](../../javascript/reference/array-from-function-array-javascript.md)|配列に似たオブジェクトまたは反復可能なオブジェクトから配列を返します。|  
|[Array.isArray 関数](../../javascript/reference/array-isarray-function-javascript.md)|オブジェクトが配列であるかどうかを示すブール値を返します。|  
|[Array.of 関数](../../javascript/reference/array-of-function-array-javascript.md)|引数として渡されたものから配列を返します。|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>メソッド  
 `Array` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[concat メソッド (Array)](../../javascript/reference/concat-method-array-javascript.md)|2 つの配列を連結した新しい配列を返します。|  
|[entries メソッド](../../javascript/reference/entries-method-array-javascript.md)|配列のキーと値のペアを含む反復子を返します。|  
|[every メソッド](../../javascript/reference/every-method-array-javascript.md)|配列のすべての要素に対して、定義されたコールバック関数が `true` を返すかどうかをチェックします。|  
|[fill メソッド](../../javascript/reference/fill-method-array-javascript.md)|指定された値を配列に設定します。|  
|[filter メソッド](../../javascript/reference/filter-method-array-javascript.md)|定義されたコールバック関数を配列の各要素に対して呼び出し、コールバック関数が `true` を返す値の配列を返します。|  
|[findIndex メソッド](../../javascript/reference/findindex-method-array-javascript.md)|コールバック関数で指定したテスト条件を満たしている最初の配列の値のインデックス値を返します。|  
|[forEach メソッド](../../javascript/reference/foreach-method-array-javascript.md)|配列の各要素に対して、定義されたコールバック関数を呼び出します。|  
|[hasOwnProperty メソッド](../../javascript/reference/hasownproperty-method-object-javascript.md)|指定した名前のプロパティがオブジェクトにあるかどうかを表すブール値を返します。|  
|[indexOf メソッド (Array)](../../javascript/reference/indexof-method-array-javascript.md)|ある値が配列内で最初に見つかった位置のインデックスを返します。|  
|[isPrototypeOf メソッド](../../javascript/reference/isprototypeof-method-object-javascript.md)|オブジェクトが、別のオブジェクトのプロトタイプ チェーンに存在するかどうかを表すブール値を返します。|  
|[join メソッド](../../javascript/reference/join-method-array-javascript.md)|配列内のすべての要素を連結して 1 つの `String` オブジェクトとして返します。|  
|[keys メソッド](../../javascript/reference/keys-method-array-javascript.md)|配列のインデックス値を含む反復子を返します。|  
|[lastIndexOf メソッド (Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|指定した値が配列内で最後に見つかった位置のインデックスを返します。|  
|[map メソッド](../../javascript/reference/map-method-array-javascript.md)|定義されたコールバック関数を配列の各要素に対して呼び出し、結果を含む配列を返します。|  
|[pop メソッド](../../javascript/reference/pop-method-array-javascript.md)|配列の最後の要素を削除し、削除した要素を返します。|  
|[propertyIsEnumerable メソッド](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|指定したプロパティがオブジェクトの一部であるかどうか、および列挙可能かどうかを表すブール値を返します。|  
|[push メソッド](../../javascript/reference/push-method-array-javascript.md)|配列に新しい要素を追加し、その要素を追加した後の配列の長さを返します。|  
|[reduce メソッド](../../javascript/reference/reduce-method-array-javascript.md)|定義されたコールバック関数を配列のすべての要素に対して呼び出し、単一の結果に累積します。 コールバック関数の戻り値は収集された結果で、コールバック関数の次の呼び出しの引数として提供されます。|  
|[reduceRight メソッド](../../javascript/reference/reduceright-method-array-javascript.md)|定義されたコールバック関数を配列のすべての要素に対して降順に呼び出し、単一の結果に累積します。 コールバック関数の戻り値は収集された結果で、コールバック関数の次の呼び出しの引数として提供されます。|  
|[reverse メソッド](../../javascript/reference/reverse-method-javascript.md)|`Array` オブジェクトの要素を反転させます。|  
|[shift メソッド](../../javascript/reference/shift-method-array-javascript.md)|配列の先頭の要素を削除し、削除した要素を返します。|  
|[slice メソッド (Array)](../../javascript/reference/slice-method-array-javascript.md)|配列の一部を返します。|  
|[some メソッド](../../javascript/reference/some-method-array-javascript.md)|配列の任意の要素に対して、定義されたコールバック関数が `true` を返すかどうかをチェックします。|  
|[sort メソッド](../../javascript/reference/sort-method-array-javascript.md)|要素の順序を並べ替えた `Array` オブジェクトを返します。|  
|[splice メソッド](../../javascript/reference/splice-method-array-javascript.md)|配列から要素を削除し、必要に応じて新しい要素を削除位置に挿入し、削除した要素を返します。|  
|[toLocaleString メソッド](../../javascript/reference/tolocalestring-method-object-javascript.md)|現在のロケールを使用して文字列を返します。|  
|[toString メソッド](../../javascript/reference/tostring-method-array.md)|配列の文字列表現を返します。|  
|[unshift メソッド](../../javascript/reference/unshift-method-array-javascript.md)|配列の先頭に新しい要素を挿入します。|  
|[valueOf メソッド](../../javascript/reference/valueof-method-array.md)|配列への参照を取得します。|  
|[values メソッド](../../javascript/reference/values-method-array-javascript.md)|配列の値を含む反復子を返します。|  
  
## <a name="see-also"></a>関連項目  
 [スクロール、パン、ズームのサンプル アプリ](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)