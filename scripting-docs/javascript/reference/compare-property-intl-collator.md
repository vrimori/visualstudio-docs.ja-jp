---
title: "compare プロパティ (Intl.Collator) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bfd222ac8d2c94efe279177e7f4d8ffdf850f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="compare-property-intlcollator"></a>compare プロパティ (Intl.Collator)
Collator の並べ替え順序を使用して 2 つの文字列を比較する関数を返します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
collatorObj.compare  
```  
  
#### <a name="parameters"></a>パラメーター  
 `collatorObj`  
 必須です。 比較に使用する `Collator` オブジェクトの名前。  
  
## <a name="remarks"></a>コメント  
 `compare` プロパティによって返される関数は、`x` と `y` という 2 つの引数を受け取り、`x` オブジェクトで指定されたオプションを使用して、`y` と `Collator` のロケール固有の比較の結果を返します。  
  
 比較の結果は次のようになります。  
  
-   `x` が並べ替え順序において `y` よりも前にある場合は -1。  
  
-   `x` が並べ替え順序において `y` と等しい場合は 0 (ゼロ)。  
  
-   `x` が並べ替え順序において `y` よりも後ろにある場合は 1。  
  
## <a name="example"></a>例  
 次の例では、`Collator` オブジェクトを作成して比較を実行します。  
  
```JavaScript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
```  
  
## <a name="example"></a>例  
 次の例では、`Collator` オブジェクトを使用して配列を並べ替えます。 この例は、ロケール固有の違いを示しています。  
  
```JavaScript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## <a name="example"></a>例  
 次の例では、`Collator` オブジェクトを使用して文字列を検索します。  
  
```JavaScript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Intl.Collator オブジェクト](../../javascript/reference/intl-collator-object-javascript.md)