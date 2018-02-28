---
title: "escape 関数 (JavaScript) |Microsoft ドキュメント"
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
- escape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encoding string objects
- Escape method
- hexadecimal
- String object, encoding
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b53a447ae6dde917c12a4711d9038136dc4500cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="escape-function-javascript"></a>escape 関数 (JavaScript)
すべてのコンピューターで読み取れるように文字列をエンコードします。 使用しないでください。  
  
## <a name="syntax"></a>構文  
  
```  
escape(charString)   
```  
  
## <a name="remarks"></a>コメント  
 必要な`charString`引数は、いずれかの`String`オブジェクトまたはリテラルをエンコードします。  
  
 **エスケープ**の内容を含む Unicode 形式で文字列値が返されます`charstring`です。 アクセント記号の文字をすべてスペース、句読点、およびその他の任意の非 ASCII 文字の置き換え`%` *xx*エンコード、場所*xx* 16 進数を表す数値と等価の文字があります。 たとえば、スペースは"%20"として返されます  
  
 255 が格納されたよりも大きい値を持つ文字、 **%u** *xxxx*形式です。  
  
> [!NOTE]
>  **エスケープ**Uniform Resource Identifier (URI) をエンコードする関数を使用する必要があります。 使用して`encodeURI`と`encodeURIComponent`代わりに機能します。  
  
 **適用されます**:[グローバル オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [encodeURI 関数](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 関数](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)   
 [unescape 関数](../../javascript/reference/unescape-function-javascript.md)