---
title: "unescape 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unescape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Unescape method
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96601fc21f47c86aec8c3702a6861c3676aacacf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="unescape-function-javascript"></a>unescape 関数 (JavaScript)
デコード`String`でエンコードされたオブジェクト、`escape`関数。 使用しないでください。  
  
## <a name="syntax"></a>構文  
  
```  
unescape(charString)   
```  
  
## <a name="remarks"></a>コメント  
 必要な`charString`引数は、`String`オブジェクトまたはリテラルをデコードできません。  
  
 `unescape`関数の内容を含む文字列値を返します`charstring`です。 % でエンコードされた文字をすべて*xx* 16 進数形式が ASCII 文字セット値で置き換えられます。  
  
 エンコードされた文字**%u** *xxxx* (Unicode 文字) の形式は 16 進エンコードを使用して Unicode 文字に置き換えられます*xxxx*です。  
  
> [!NOTE]
>  `unescape` Uniform Resource Identifier (URI) をデコードする関数を使用する必要があります。 使用して`decodeURI`と`decodeURIComponent`代わりに機能します。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[グローバル オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [decodeURI 関数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 関数](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [escape 関数](../../javascript/reference/escape-function-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)