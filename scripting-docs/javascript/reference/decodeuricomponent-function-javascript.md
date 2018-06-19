---
title: decodeURIComponent 関数 (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- decodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURIComponent method
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef7bdcd374a328bad632381d19e9823853d37f01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636192"
---
# <a name="decodeuricomponent-function-javascript"></a>decodeURIComponent 関数 (JavaScript)
エンコードされていないバージョンのエンコードされたコンポーネントの Uniform Resource Identifier () を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>コメント  
 必要な`encodedURIString`引数には、エンコードされた URI コンポーネントを表す値です。  
  
 完全な URI の一部である、URIComponent です。  
  
 場合、`encodedURIString`が有効でない、URIError が発生します。  
  
## <a name="example"></a>例  
 次のコードでは、最初にエンコードし、URI をデコードします。  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [decodeURI 関数](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI 関数](../../javascript/reference/encodeuri-function-javascript.md)