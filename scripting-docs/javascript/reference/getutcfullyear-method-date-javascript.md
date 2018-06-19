---
title: getUTCFullYear メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
- getUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getUTCFullYear method
- Date object
- UTCFullYear method
- dates, UTC
- UTC dates, returning
- Full Year method
- UTC dates, getting
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8268631a96eed1f61ef4ba908b78680c8522096
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636852"
---
# <a name="getutcfullyear-method-date-javascript"></a>getUTCFullYear メソッド (Date) (JavaScript)
世界協定時刻 (UTC) を使用して、年を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 年を 4 桁の数値として返します。 2 桁の数字として指定された年、`Date`コンス トラクターまたは`setFullYear`想定する、20 世紀のため、「5/14/12」を付ける`getUTCFullYear`「1912」を返します。  
  
## <a name="remarks"></a>コメント  
 ローカル時刻を使用して、年を取得する、`getFullYear`メソッドです。  
  
## <a name="example"></a>例  
 `getUTCFullYear` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getFullYear メソッド (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear メソッド (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear メソッド (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)