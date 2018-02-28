---
title: "decodeURI 関数 (JavaScript) |Microsoft ドキュメント"
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
- decodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURI method
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97291142083ae88c7dc84d9cd08af5c3c39ff9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuri-function-javascript"></a>decodeURI 関数 (JavaScript)
エンコードされていないバージョンのエンコードされた Uniform Resource Identifier () を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
decodeURI(URIstring)  
```  
  
## <a name="remarks"></a>コメント  
 必要な`URIstring`引数は、エンコードされた URI を表す値です。  
  
 使用して、`decodeURI`関数ではなく、非推奨`unescape`関数。  
  
 `decodeURI`関数は、文字列値を返します。  
  
 場合、`URIString`が有効でない、URIError が発生します。  
  
 **適用されます**:[グローバル オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>例  
 次のコードでは、まず URI コンポーネントをエンコードし、デコードされます。  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [decodeURIComponent 関数](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [encodeURI 関数](../../javascript/reference/encodeuri-function-javascript.md)   
 [Global オブジェクト](../../javascript/reference/global-object-javascript.md)