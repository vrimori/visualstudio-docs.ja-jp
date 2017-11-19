---
title: "getFullYear メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- Date object
- getFullYear method
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 211d6c86435e39eb75b9b1ce3415738541ca07db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getfullyear-method-date-javascript"></a>getFullYear メソッド (Date) (JavaScript)
ローカル時刻を使用して、年を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getFullYear()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 年 (4 桁の数値)。 たとえば、1976 年は、1976年として返されます。 2 桁の数字として指定された年、`Date`コンス トラクターまたは`setFullYear`想定する、20 世紀のため、「5/14/12」を付ける`getFullYear`「1912」を返します。  
  
## <a name="remarks"></a>コメント  
 世界協定時刻 (UTC) を使用して、年を取得する、`getUTCFullYear`メソッドです。  
  
## <a name="example"></a>例  
 次の例では、使用、 **getFullYear**メソッドです。  
  
```JavaScript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getUTCFullYear メソッド (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear メソッド (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear メソッド (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)