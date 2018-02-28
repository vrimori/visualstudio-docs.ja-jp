---
title: "split メソッド (String) (JavaScript) |Microsoft ドキュメント"
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
- split
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- split method
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea90dda2e8e4d52451af247d139eeee44f83917
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="split-method-string-javascript"></a>split メソッド (String) (JavaScript)
指定した区切り記号を使用して文字列を部分文字列に分割し、配列として返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## <a name="parameters"></a>パラメーター  
 `stringObj`  
 必須です。 分割する `String` オブジェクトの名前またはリテラル文字列を指定します。 このオブジェクトがによって変更されない、**分割**メソッドです。  
  
 `separator`  
 省略可能です。 文字列または**正規表現**文字または文字列を分離することで使用する文字を識別するオブジェクト。 省略した場合、文字列全体を含む単一要素の配列が返されます。  
  
 `limit`  
 省略可能です。 配列に返される要素の数を制限する値を指定します。  
  
## <a name="return-value"></a>戻り値  
 結果、**分割**メソッドは各ポイントで分割してできた文字列の配列では、`separator`で発生した`stringObj`です。 `separator` は、配列要素の一部としては返されません。  
  
## <a name="example"></a>例  
 次の例では、使用、**分割**メソッドです。  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [concat メソッド (String)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [スクロール、パン、ズームのサンプル アプリ](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)