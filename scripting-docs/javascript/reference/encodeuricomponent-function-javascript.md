---
title: encodeURIComponent 関数 (JavaScript) |Microsoft ドキュメント
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
- encodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURIComponent method
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56680e9bcfe1de61d8a1eabd0ff8d2eced01d603
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636432"
---
# <a name="encodeuricomponent-function-javascript"></a>encodeURIComponent 関数 (JavaScript)
有効なコンポーネントの識別子 URI (Uniform Resource) としてテキスト文字列をエンコードします。  
  
## <a name="syntax"></a>構文  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>コメント  
 必要な`encodedURIString`引数には、エンコードされた URI コンポーネントを表す値です。  
  
 `encodeURIComponent`関数は、エンコードされた URI を返します。 結果を渡した場合`decodeURIComponent`、元の文字列が返されます。 `encodeURIComponent`関数は、すべての文字をエンコード、文字列などのパスを表す場合は注意 **/folder1/folder2/default.html**です。 スラッシュ文字では、エンコードはされ、web サーバーに要求として送信された場合は無効になります。 使用して、`encodeURI`文字列が 1 つの URI コンポーネントよりも多く含まれている場合に機能します。  
  
## <a name="example"></a>例  
 次のコードでは、まず URI コンポーネントをエンコードし、デコードされます。  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [decodeURI 関数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 関数](../../javascript/reference/decodeuricomponent-function-javascript.md)