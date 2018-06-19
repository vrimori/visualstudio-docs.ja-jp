---
title: getTime メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
- getTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetTime method
- time method
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a31e542445e89a0e2f3364d36ae44f8d2d4cf9bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636662"
---
# <a name="gettime-method-date-javascript"></a>getTime メソッド (Date) (JavaScript)
ミリ秒単位で時間の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getTime()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 午前 0 時、1970 年 1 月 1 日と時刻の値の間 (ミリ秒) の数を返します、`Date`オブジェクト。 日付の範囲は、午前 0 時、1970 年 1 月 1 日の約 285,616 年です。 負の数値は、1970 年以前の日付を示します。  
  
## <a name="remarks"></a>コメント  
 複数の日付と時刻の計算を行う場合は、日、時間、または分でミリ秒単位の数と同じ変数を定義します。 例:  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 参照してください[を計算する日付と時刻 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)の使用方法に関する詳細について、`getTime`メソッドです。  
  
## <a name="example"></a>例  
 `getTime` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [setTime メソッド (Date)](../../javascript/reference/settime-method-date-javascript.md)