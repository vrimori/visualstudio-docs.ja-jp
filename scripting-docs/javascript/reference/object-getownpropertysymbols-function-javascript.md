---
title: "Object.getOwnPropertySymbols 関数 (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bcddba77305e30e4c5ae13f6b1fc5c9385b7108
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Object.getOwnPropertySymbols 関数 (JavaScript)
オブジェクトの独自のシンボル プロパティを返します。 オブジェクトの独自のシンボル プロパティは、オブジェクトのプロトタイプから継承されたものではなく、そのオブジェクトに直接定義されたプロパティです。  
  
## <a name="syntax"></a>構文  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 独自のシンボルを含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 オブジェクトの独自のシンボルを含む配列。  
  
## <a name="remarks"></a>コメント  
 オブジェクトのシンボル プロパティを取得するには、`Object.getOwnPropertySymbols` を使用する必要があります。 `Object.getOwnPropertyNames` はシンボル プロパティを返しません。  
  
## <a name="example"></a>例  
 次のコード例では、オブジェクトのシンボル プロパティを取得する方法を示しています。  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]