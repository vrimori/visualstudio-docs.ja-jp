---
title: コレクション (JavaScript) | Microsoft Docs
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
ms.assetid: 23c26185-6a7b-4b69-9d22-63e1841b4905
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fab554f50f6d2fcdac92c562333e625dc0eb32f6
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
ms.locfileid: "27783053"
---
# <a name="collections-javascript"></a>コレクション (JavaScript)
値とオブジェクトを格納するには、コレクション オブジェクト [Map](../../javascript/reference/map-object-javascript.md)、[Set](../../javascript/reference/set-object-javascript.md)、[WeakMap](../../javascript/reference/weakmap-object-javascript.md) を使用できます。 これらのオブジェクトには、インデックスの代わりにキーまたは値を使用してメンバーを追加および取得するための便利なメソッドが用意されています。 インデックスを使用してコレクションのメンバーにアクセスするには、`Array` オブジェクトを使用します。 詳しくは、「[配列の使用](../../javascript/advanced/using-arrays-javascript.md)」をご覧ください。  
  
> [!CAUTION]
>  `Map`、`Set`、および `WeakMap` は、Internet Explorer 11 より前のバージョンのブラウザーではサポートされていません。 バージョン サポートについて詳しくは、「[バージョン情報](../../javascript/reference/javascript-version-information.md)」をご覧ください。  
  
## <a name="using-collections"></a>コレクションの使用  
 `Map` オブジェクトと `WeakMap` オブジェクトには、キーと値のペアが格納されます。このキーを使用すると、メンバーを追加、取得、および削除できます。 キーと値の型は任意です。 `Set` オブジェクトには、任意の型の値が格納されます。  
  
 `Map` オブジェクトおよび `Set` オブジェクトでは、`forEach` メソッドを使用してコレクション メンバーを列挙し、`size` メソッドを使用してコレクションのサイズをチェックできます。 これに対し、`WeakMap` オブジェクトは列挙可能ではありません。 このコレクションの場合、キー参照が弱く保持されます。 アプリがコレクションの各メンバーをメモリ内に保持する必要があるかどうかをガベージ コレクターで決定するには、`WeakMap` を使用します。 これは、キャッシュのシナリオでキャッシュされたオブジェクトが非常に大きく、必ずしもオブジェクトをメモリ内に保持しなくてよい場合などに役立つことがあります。 場合によっては、メモリ リークを防ぐために、このオブジェクトを使用できます。  
  
 次の例は、`Map` オブジェクトを使用する方法を示しています。 この例では、`get` と `forEach` の両方を使用してメンバーにアクセスします。 `forEach` 内のコールバック関数では 3 つのパラメーターを受け取ることができます。これらは、現在のコレクション要素の値、現在の要素のキー、およびコレクション オブジェクト自体を提供します。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
document.write(m.get(2));  
document.write("<br />");  
  
m.forEach(function (value, key, mapObj) {  
    document.write(value.toString() + "<br />");  
});  
  
// Output:  
// red  
  
// black  
// red  
// 2  
// 3  
  
```  
  
 `WeakMap` の使用は `Map` に似ていますが、メンバーの取得に `get` のみを使用できる点が異なります。 例については、[WeakMap](../../javascript/reference/weakmap-object-javascript.md) オブジェクトをご覧ください。  
  
 次の例は、`Set` オブジェクトを使用する方法を示しています。 この例では、コールバック関数が受け取るパラメーターは 1 つのみです。このパラメーターは、現在のコレクション要素の値を提供します。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (value) {  
    document.write(value.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="see-also"></a>参照  
 [高度な JavaScript](../../javascript/advanced/advanced-javascript.md)