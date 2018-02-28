---
title: "lastIndexOf メソッド (String) (JavaScript) |Microsoft ドキュメント"
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
- lastIndexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndexOf method, string
- string, lastIndexOf method
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fa0f35e970435a4d0296493c20afdeaac128cae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-string-javascript"></a>lastIndexOf メソッド (String) (JavaScript)
文字列の最後に見つかった部分文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## <a name="parameters"></a>パラメーター  
 `strObj`  
 必須です。 `String` オブジェクトまたは文字列リテラル。  
  
 `substring`  
 必須です。 検索する部分文字列です。  
  
 `startindex`  
 省略可能です。 検索を開始する位置を示すインデックス。 省略した場合、文字列の末尾から検索を開始します。  
  
## <a name="remarks"></a>コメント  
 **LastIndexOf**メソッド内の部分文字列の先頭を示す整数値を返します、`String`オブジェクト。 部分文字列が見つからない場合、-1 が返されます。  
  
 `startindex` に負の値を指定すると、`startindex` は 0 として扱われます。 最大の文字位置のインデックスよりも大きい場合は、最大の可能なインデックスとして扱われます。  
  
 検索すると、文字列の最後の文字で始まるが実行されます。 このメソッドは、それ以外の場合と同じ**indexOf**です。  
  
 次の例では、使用、 **lastIndexOf**メソッドです。  
  
```JavaScript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [indexOf メソッド (String)](../../javascript/reference/indexof-method-string-javascript.md)