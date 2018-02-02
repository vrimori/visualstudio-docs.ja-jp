---
title: "getUTCHours メソッド (Date) (JavaScript) |Microsoft ドキュメント"
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
- getUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- UTC times, returning
- getUTCHours method
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47fe66e6eecb9e3aaa53f0d0988631062676d17
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="getutchours-method-date-javascript"></a>getUTCHours メソッド (Date) (JavaScript)
内の時間の値を取得、`Date`オブジェクト世界協定時刻 (UTC) を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 0 から午前 0 時からの経過時間の数を示す 23 の整数を返します。 時刻が午前 1時 00分: 00 よりも前にある場合は、0 が返されます。 場合、`Date`時刻を指定しないでオブジェクトが作成された、既定では、1 時間は 0 (utc) 時刻。 この時刻は 0 以外をする可能性があります他のタイム ゾーン。  
  
## <a name="remarks"></a>コメント  
 午前 0 時からの数を取得する時間が経過したローカル時刻を使用して、`getHours`メソッドです。  
  
## <a name="example"></a>例  
 `getUTCHours` メソッドの使用例を次に示します。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(date2.getUTCHours());  
  
// Output (in the PST time zone):  
// 15 
// 2  
```  
  
## <a name="requirements"></a>必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>参照  
 [getHours メソッド (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours メソッド (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours メソッド (Date)](../../javascript/reference/setutchours-method-date-javascript.md)
