---
title: "encodeURI 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: encodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: encodeURI method
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf9bbdf34c0481c889d1176bc32ab0246a333a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuri-function-javascript"></a>encodeURI 関数 (JavaScript)
テキスト文字列として、有効な識別子 URI (Uniform Resource) のエンコードします。  
  
## <a name="syntax"></a>構文  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## <a name="remarks"></a>コメント  
 必要な`URIString`引数は、エンコードされた URI を表す値です。  
  
 `encodeURI`関数は、エンコードされた URI を返します。 結果を渡した場合`decodeURI`、元の文字列が返されます。 `encodeURI`関数は、次の文字をエンコードしません:":"、「/」、「;」と"?"。 使用して`encodeURIComponent`これらの文字をエンコードします。  
  
## <a name="example"></a>例  
 次のコードでは、最初にエンコードし、URI をデコードします。  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [decodeURI 関数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 関数](../../javascript/reference/decodeuricomponent-function-javascript.md)