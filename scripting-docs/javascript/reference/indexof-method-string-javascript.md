---
title: "indexOf メソッド (String) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: indexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- indexOf method, string
- string, indexOf method
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecd96acb21f9d7711f9ee00dbf1c1bb70705c0d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-string-javascript"></a>indexOf メソッド (String) (JavaScript)
最初に見つかった部分文字列の位置を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## <a name="parameters"></a>パラメーター  
 `strObj`  
 必須です。 A`String`オブジェクトまたは文字列リテラルです。  
  
 `subString`  
 必須です。 文字列から検索する部分文字列  
  
 `startIndex`  
 省略可能です。 `String` オブジェクトの検索の開始位置を示すインデックス。 省略した場合は、文字列の先頭から検索が開始されます。  
  
## <a name="remarks"></a>コメント  
 **IndexOf**内の部分文字列の先頭を返します、`String`オブジェクト。 検索文字列が見つからなかった場合は、-1 が返されます。  
  
 `startindex` に負の値を指定すると、`startindex` は 0 として扱われます。 最も大きいインデックスを超える場合、最も大きいインデックスとして扱われます。  
  
 検索は左から右へと行われます。 このメソッドは、それ以外の場合と同じ**lastIndexOf**です。  
  
## <a name="example"></a>例  
 次の例では、使用、 **indexOf**メソッドです。  
  
```JavaScript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [lastIndexOf メソッド (String)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [スクロール、パン、ズームのサンプル アプリ](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)