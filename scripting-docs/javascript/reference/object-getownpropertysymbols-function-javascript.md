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
ms.openlocfilehash: 2cc47ae365841332f11cb02da1469a4c9fff80c3
ms.sourcegitcommit: abae48f476832f79cc2c5bac43bb1226d3fe4e48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2018
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Object.getOwnPropertySymbols 関数 (JavaScript)
オブジェクトの独自のシンボル プロパティを返します。 オブジェクトの独自のシンボル プロパティは、オブジェクトのプロトタイプから継承されたものではなく、そのオブジェクトに直接定義されたプロパティです。  
  
## <a name="syntax"></a>構文  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 必須。 独自のシンボルを含むオブジェクト。  
  
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
  
console.log(symbols[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]