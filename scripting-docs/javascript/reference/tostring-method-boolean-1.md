---
title: "toString メソッド (Boolean) 1 |Microsoft ドキュメント"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17dd9503e4e09aafca3d153662bf7487538cda3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-boolean-1"></a>toString メソッド (Boolean) 1
オブジェクトの値を表す文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
boolean.toString()  
```  
  
## <a name="parameters"></a>パラメーター  
 `boolean`  
 必須です。 文字列形式を取得する対象のオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 ブール値が場合`true`、"true"を返します。 それ以外の場合、"false"を返します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 次の例では、使用、 **toString**メソッドです。  
  
```JavaScript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]